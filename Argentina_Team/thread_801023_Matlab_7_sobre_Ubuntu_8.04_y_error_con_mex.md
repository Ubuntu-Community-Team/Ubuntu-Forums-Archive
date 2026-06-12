---
title: "Matlab 7 sobre Ubuntu 8.04 y error con mex"
date: 2008-05-20
forum: Argentina Team
---

### Post by anaGP on 2008-05-20
Tengo instalado el matlab 7 sobre linux. Uso la distribución kubuntu (Ubuntu 8.04 kernel 2.6.24 - 16- generic).
Matlab no reconoce el mex -setup (da un error de licencia).
Pero en línea de comando del linux sí funciona bien el mex -setup.
¿Alguien puede darme alguna sugerencia?
Muchas gracias
AnaGP
 

//////////////////////
El mensaje de error que da Matlab:  /////////

Bienvenidos. A trabajar con TrueTime.

Espere por favor ...

Todo bien hasta aca ...

Warning: Unrecognized MATLAB option "setup".

 

License Manager Error -2.

Invalid license file syntax

Feature:       MATLAB

License path:  /usr/local/matlab7/bin/mex

FLEXlm error:  -2,413

For further information, refer to the FLEXlm End User Manual,

available at "www.macrovision.com".

 

Check the MATLAB INCREMENT line in your license file,

or make sure you have a USE_SERVER line instead

of INCREMENT lines.  Also check to be sure there is

a carriage return at the end of the USE_SERVER line.

 

For more information, see The MathWorks Support page at

[http://www.mathworks.com/support](http://www.mathworks.com/support) and search for

"license manager error -2"

??? Error using ==> mex

Unable to complete successfully

 

Error in ==> matlabrc at 197

mex -setup

/////////////////////////
Lo agregado al final del matlabrc para que Matlab reconozca una librería llamada Truetime   ////////////

disp('Bienvenidos. A trabajar con TrueTime.')
disp('Espere por favor ...')
addpath([getenv('TTKERNEL')])
init_truetime;
disp('Todo bien hasta aca ...');

mex -setup

make_truetime;

---

