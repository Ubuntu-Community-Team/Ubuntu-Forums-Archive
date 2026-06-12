---
title: "Wine con juegos no conocidos."
date: 2007-08-31
forum: Argentina Team
---

### Post by valucha on 2007-08-31
[COLOR="DarkOrchid"]Hola, yo sigo tratando de hacerle funcionar todo a mi tía. Cada vez estoy más cerca .
Y ahora tengo otro problema,...
Ellos jugaban en Windows a unos juegos re viejos que tiene en un cd y trato de hacerlos correr con Wine y no hay caso.
Paso a comentar los síntomas.

Cuando trato de ejecutarlo me dice lo siguiente:
bautista@bautista-desktop:~$ wine PRE2.EXE
wine: could not load L"c:\\windows\\system32\\PRE2.EXE": Module not found

Parece un error re común,pero no tengo idea de cómo hacerlo funcionar.
Si me ayudan mejor.


Probé también con Cedega, pero sinceramente no sé ni como se usa..


Muchas gracias
Valucha[/COLOR]

---

### Post by kowal on 2007-08-31
Tenés idea de como se llama el juego?
Si es muy viejo el juego y corre bajo MS-DOS, podés usar DOSBox (con algún front-end) que permite ejecutar juegos/programas de DOS en Linux a la perfección.

También podés instalarle unos emuladores con algunos jueguitos, nunca falla para entretener a los niños :P

Saludos

---

### Post by juanman on 2007-09-01
> **valucha said:**
> [COLOR="DarkOrchid"]
Cuando trato de ejecutarlo me dice lo siguiente:
bautista@bautista-desktop:~$ wine PRE2.EXE
wine: could not load L"c:\\windows\\system32\\PRE2.EXE": Module not found
[/COLOR]

Es porque primero debes ubicarte en el directorio donde esta el ejecutable. Mas facil, abres el administrador de archivos y haces doble click, probablemente te lo abrira con wine; si te pregunta abrirlo con q, escribe wine y pone q se abra siempre con este.
Ahora si no se abre nada, es porque hubo algun error; para ver el error esta bueno poder abrirlo desde consola, lo mas comodo es estando en nautilus en el directorio del .exe usar [este truco]("http://www.hachemuda.com/2007/05/16/truco-de-nautilus-abrir-terminal-aqui-sin-instalar-ningun-script/"), lo q te abrira la consola en el directorio adecuado y ahi si haces wine programa.exe. Recuerda q si escribes wine pro (las primeras letras y presionas TAB, te autocompletara lo q sigue.)

Si el juego es de DOS te funcionara seguro con el dosbox aunq debe andar mas lento me parece xq es un emulador; y wine, con su nombre lo dice no es un emulador (no emula una pc completa), xq lo q es mas rapido (Wine Is Not a Emulator)

Saludos

---

### Post by FlyerDie on 2007-09-01
> **kowal said:**
> Tenés idea de como se llama el juego?
Si es muy viejo el juego y corre bajo MS-DOS, podés usar DOSBox (con algún front-end) que permite ejecutar juegos/programas de DOS en Linux a la perfección.

También podés instalarle unos emuladores con algunos jueguitos, nunca falla para entretener a los niños :P

Saludos

Sin ser yo en interesado (pero si un viejo jugador de juegos jajaja) el ejecutable PRE2.EXE es del Prehistoric 2...un juego muy adictivo en su momento.
Ahora me mataste si es bajo DOS, ya que lo corria en win98 en su momento, pero quiero creer que en realidad era DOS.

---

### Post by leo_rockway on 2007-09-01
el pre2.exe es el prehistoric 2 y corria bajo DOS.

proba el dosbox... quizas se complique hacer funcionar el sonido, pero el juego tiene que correr.

de todas formas... podrias hacer la prueba tb de instalar equivalentes. dejarle el pre2 pero tb el supertux (que es clon de mario, no de pre2... pero no importa :-P)

el supertux es tan bueno juego como el prehistoric 2 :-D

---

### Post by valucha on 2007-09-01
[COLOR="DarkOrchid"]En la computadora ya tienen como 50 juegos nativos de Linux, pero realmente parece que juegan bastante.

Bueno, pude hacer andar el prehistorik con el DOSBOX el cual tenía un error pero solucioné reiniciando cual Windows.

Les dejo una guçia que me ayudó bastante que encima da links a juegos viejitos.
Saludos:

[http://palermi.wordpress.com/2006/06/30/abandoware-en-ubuntu/](http://palermi.wordpress.com/2006/06/30/abandoware-en-ubuntu/)[/COLOR]

---

### Post by valucha on 2007-09-03
[COLOR="DarkOrchid"]Vuelvo con otro problema.
No sé como poner el DOSBox en pantalla completa.

Alguien sabe?[/COLOR]

---

### Post by leo_rockway on 2007-09-03
> **valucha said:**
> [COLOR="DarkOrchid"]Vuelvo con otro problema.
No sé como poner el DOSBox en pantalla completa.

Alguien sabe?[/COLOR]

alt+enter

---

