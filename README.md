# Mi Proyecto

Proyecto individual para practicar el ciclo de vida basico de Git.

## Comandos que use en este proyecto

Explicacion, en mis propias palabras, de cada comando del ejercicio.

### git init

Convierte una carpeta normal en un repositorio de Git. Crea una carpeta oculta
`.git` dentro del proyecto, que es donde Git guarda todo el historial. Antes de
`init` la carpeta no tiene memoria; despues, Git empieza a vigilar los archivos.
Solo se ejecuta una vez por proyecto.

### git status

El que mas use. Muestra en que estado esta cada archivo: cuales Git no conoce
todavia (`untracked`, en rojo), cuales cambie pero no he marcado, y cuales ya
estan listos para el commit (en verde). Sirve para saber donde estoy parado
antes de hacer cualquier cosa.

### git add

Marca los cambios que quiero incluir en el proximo commit, o sea los pasa al
"area de staging". Es un paso intermedio a proposito: no todo lo que modifico
tiene que entrar en el mismo commit, `add` me deja escoger. Despues de un `add`,
el archivo pasa en `git status` de "Changes not staged" a "Changes to be
committed".

### git commit

Guarda de forma permanente en el historial lo que estaba en staging. Cada commit
es una foto del proyecto en ese momento, con un identificador llamado hash, mi
nombre, la fecha y el mensaje que escribo con `-m`. El commit es local: todavia
no esta en GitHub.

### git push

Sube al repositorio remoto de GitHub los commits que ya tengo en mi computador.
La primera vez use `git push -u origin main`; ese `-u` deja enlazada mi rama
local con la del remoto, y por eso despues basta con escribir `git push` solo.
Solo sube lo que ya tiene commit hecho.

### git diff

Muestra linea por linea que cambio respecto al ultimo commit. Lo que agregue
sale en verde con `+` delante, y lo que borre en rojo con `-`. Lo uso antes del
`add` para revisar que voy a guardar y no subir algo por error.

### git log

Muestra el historial de commits, del mas reciente al mas antiguo, con el hash,
el autor, la fecha y el mensaje. Con `git log --oneline --graph` sale la version
resumida: un commit por linea y un dibujo de como se conectan.

### Deshacer cambios

De los comandos para deshacer, el que mas me sirvio fue
`git restore --staged <archivo>`: saca un archivo del area de staging despues de
un `git add`, pero **sin borrar el cambio**. El archivo vuelve a aparecer como
modificado y sin marcar. Es el arreglo tipico cuando agrego algo que no queria
incluir en ese commit.

Los otros que probe:

- `git restore <archivo>` — descarta los cambios que no he commiteado y deja el
  archivo como estaba en el ultimo commit. Este si borra el trabajo.
- `git reset --soft HEAD~1` — deshace el ultimo commit pero conserva los cambios
  en staging, como si nunca lo hubiera escrito.
- `git checkout <hash> -- <archivo>` — trae un archivo tal como estaba en un
  commit anterior, sin tocar el resto del proyecto.
