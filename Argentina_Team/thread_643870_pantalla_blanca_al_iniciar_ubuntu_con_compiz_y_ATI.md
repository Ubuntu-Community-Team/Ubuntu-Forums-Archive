---
title: "pantalla blanca al iniciar ubuntu con compiz y ATI"
date: 2007-12-18
forum: Argentina Team
---

### Post by melvinlopez06 on 2007-12-18
hola a todos, la loca con ATI, sino es un problema es otro, aunque en realidad [despues de este otro problema]("http://ubuntuforums.org/showthread.php?p=3945571") me di cuenta que no era ati pero de seguro le cai mal porque hoy si me ataco.

Resulta que despues de arreglar lo del powernowd la maquina funciono chivisimo, cero problemas y todo el dia estuve trabajando con ella, el compiz iba de lujo, suave y sin problemas con los ultimos drivers de ATI, tambien tenia aceleracion grafica, pero hoy me pasa eso, cuando inicio con ubuntu carga todo normal, da la pantalla de login y entro, puedo ver el papel tapiz del escritorio y cuando termina de cargar se queda en blanco, solo puedo ver la silueta de los paneles superior e inferior y el desktop tapado con un cuadro gris que cubre toda la pantalla.

No veo iconos, ni menus ni nada, el cubo gira pero siempre con los recuadros grises cubriendo toda la pantalla, de seguro algo ocurrio con compiz, trate de iniciar con gnome a prueba de fallos y siguio lo mismo.

El sistema se ejecuta, los programas se cargan y puedo desplazarme por las consolas ctrl+alt+F* pero no veo nada grafico mas que esos paneles grises tapando todo.

Lo ultimo que hice fue actualizar el sistema, habian 145 actualizaciones disponibles y entre ellas vi varios paquetes de compiz

Que puede ser, como desactivo compiz para probar si funciona sin el.
Sugerencias, a ver si me hechan la manito :)

---

### Post by sajnox on 2007-12-18
Hola,

Yo tambien sufro las ATI, hace rato que no pruebo los nuevos drivers, la ultima vez que los use fue a travez de envy y no me termino de convencer el rendimiento que tenian.

Por el lado de tu problema,

1) Probaste reiniciar X (se que no es el mejor modo linux pero a veces funciona) ctrl + alt + backspace

2) Hacete un backup del xorg.conf y reconfiguralo a ver que pasa

para hacer el backup 

```
sudo cp /etc/X11/xrog.conf /etc/X11/xorg.back
```

Para reconfigurar

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Y despues de eso, si reinicias x = ctrl + alt + backspace

contanos que hace

---

### Post by melvinlopez06 on 2007-12-19
te cuento sajnox que sigue lo mismo, la primera vez probe reiniciando las X, y nel, posteriormente reconfigure y reinicie las X otra vez y sigue igual.

Me late que es compiz quien esta dando lata, buscare como desactivarlo y porque esta pasando eso.

alguna otra idea ??
imagino que tiene algo que ver ATI porque en casa tengo ubuntu tambien, con compiz y todo eso, pero con una nvidia y todo tranquilo, jamas me ha pasado algo similar, incluso despues de las actualizaciones que hice casi junto con esta maquina de mi work.

---

### Post by Moonlit Knight on 2007-12-19
Instalá el paquete xserver-xgl . Yo tengo la ati onboard xpress y si no es con ese paquete no funciona o funciona mal el compiz, esto es porque las atis todavía no tienen buen soporte con aiglx.

Hacé esto sudo apt-get install xserver-xgl 

Si no podés abrir una consola apretá ctrl + alt + F1 y te va a aparecer el login en modo texto, logueate, y después poné el comando. Reiniciás y decime como te fue.

---

### Post by faktorqm on 2007-12-19
estemmm hace una cosa. cuando reconfiguras el x, y te sigue pasando lo mismo, apreta ctrl + alt + F2, logueate, y escribi "metacity --replace".
Volve a la interfaz grafica con ctrl + alt + f7. si se ve, desde ahi podes hacer cosas con el envy. si sigue sin verse, hace esto:

ctrl + alt + F2, logueate y edita el archivo con nano:

"sudo nano /etc/X11/xorg.conf"

En la seccion driver le pones vesa. grabas y reinicias.
Cuando reinicies probablemente te pase lo mismo, entonces ahi si volves a hacer ctrl + alt + f2, te logueas, "metacity --replace" y volves con crtl + alt + f7. ahi  se te tiene que ver si o si. salu2!

---

### Post by melvinlopez06 on 2007-12-19
bueno solucionado el problema.
¿que era el problema?
pues no lo se, al final no se si lo que estaba mal era el compiz o los drivers de ati o los drivers vesa.

ahorita escribo desde ubuntu ya todo arreglado, que hice

1. probe lo que me dijo Sajnox, y no funciono ni siquiera reconfigurando el xorg.

2. desabilite xgl, coloque un archivo llamado "disable" (sin las comillas) en la dir ~/.config/xserver-xgl/ para desabilitarlo, reinicie las X y lo mismo, seguian los cuadros grises tapando la pantalla.

3. volvi a reconfigurar el xorg y lo edite con nano en la consola y cambie el driver de ati por vesa, nada, inicio pero la misma *****, y compiz ya no funcionaba.

4. volvia a la consola y edite el xorg con nano, y puse de driver "mesa" (equivocado obvio) y salio al rescate las X con antibalas, cargo en modo grafico bajo y configure monitor y resolucion, utilizando drivers libres de ati radeon, y nada, luego probe drivers propietarios de las radeon y seguia lo mismo (creo que eran los ultimos que instale, los que soportan AIGLX).

5. Desesperado (ya me artaba la colera) entre al Gestor de Controladores Restringidos y desactive ATI, reinice y todo =, los mismos paneles chucos, edite con nano el xorg y puse mesa otra vez, cargo el X antibalas (en realidad funciona de maravilla esto) y volvi a activar los drivers propietarios de ati.

6. me pidio reiniciar y aqui estoy, con los viejos drivers de ati, sin AIGLX, sin compiz, con el tema human de ubuntu (se lo cambie en los pasos anteriores), con aceleracion grafica pero sin mi cubo :'(

Recomendaciones:
Ati es una mier*** , esperemos que mejore, yo en casa sigo con nvidia, lastimosamente esta maquina del work tiene ati.

PD: antes de todo esto di un apt-get upgrade en la consola y el sistema actualizo las linux-headers, tendra algo que ver esto ??, digo porque recuerden que para instalar los nuevos drivers de ati el instalador compila un par de cosas utilizando las cabeceras.

bueno esa es mi historia !! :)
y sali ileso de ella !! buaaaaaalllaaaaaa jeje :P

---

### Post by melvinlopez06 on 2007-12-19
bueno ya tengo el cubo de nuevo, no sabia que instalando el paquete xserver-xgl se podia ejecutar compiz, de haberlo sabido ni siquiera me hubiera mosqueado en instalar los ultimos drivers de Ati.

pero bien, ki toy ya, solo que se me desconfiguro el teclado pero ya lo arregle.
otra experiencia mas para la bolsita de conocimiento :D
saludos a todos y gracias por su ayuda

---

### Post by faktorqm on 2007-12-20
si, tanto para nvidia y para ati cada vez que actualizas el kernel tenes que reinstalar los drivers. Esto es por que tanto nvidia como ati NO LIBERAN SUS DRIVERS, y estamos trabajando con dirvers propietarios. Seguro quieren esconder fallas de hardware, de programacion en el driver, y demas menesteres propios de una compañia capitalista que debe ganar plata, sin importar como. Salu2!

---

