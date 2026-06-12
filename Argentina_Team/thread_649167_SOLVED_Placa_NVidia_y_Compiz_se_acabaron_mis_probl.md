---
title: "SOLVED Placa NVidia y Compiz se acabaron mis problemas"
date: 2007-12-24
forum: Argentina Team
---

### Post by rojojuan on 2007-12-24
Estimados foreros:
He recibido un regalo de Navidad! Y lo subo por si alguien tiene problemas con su placa NVidia.
Quiero comentarles la mala experiencia que tuve al usar Firefox. Dejé varios mensajes en el foro por los problemas que tenía al colgarse el navegador, que tenía que reiniciar, etc. 
La cosa mejoró cuando desactivé Compiz. 
Después con otra actualización se despelotó más el sistema, se colgaba más seguido.
Tengo un AMD X2 3800+
Investigando y tomando datos del foro, desactivé powernowd y la situación mejoró, pero en Internet, de  vez en cuando se seguía colgando.
Había visto algunas referencias a problemas entre Nvidia y Compiz.
En la página de Nvidia ví que había un nuevo driver para mi placa de video (7300gs) y que claramente decía que arreglaba algunas incompatibilidades que tenía con Compiz.
Decidí instalar el nuevo driver, con lo que todos los problemas ahora desaparecieron.
Puedo usar Compiz sin problema alguno.
Para la actualización borré el Envy viejo e instalé el nuevo (0.0.9 para Ubuntu), que se conecta para instalar el último driver de la página de Nvidia.
Con el Envy primero hay que borrar el driver anterior. Yo tenía el 100,14,19. Después ejecutar Envy.
Firefox me consume 100 megas, sin ocasionar problemas. 

Cambios en esta versión de Nvidia:

Controlador de pantalla para Linux – x86
Versión: 169.07
Sistema operativo: Linux x86
Fecha: 20.12.2007
Aspectos destacados de la versión 
Se ha añadido soporte para GeForce 8800 GT, GeForce 8800 GTS 512 y GeForce 8800M. 
Se ha añadido el controlador de CUDA al archivo .run. 
Se ha mejorado el soporte de modesetting en las GPU Quadro/GeForce Serie 8. 
Se han corregido varios problemas de renderizado de X. 
Se han corregido problemas de desplazamiento de los objetos dibujables (Drawable) ARGB de X en Qt. 
Se ha mejorado el soporte de modesetting para HDMI, HDTV y DVI entrelazado. 
Se han corregido problemas de estabilidad con algunas GPU GeForce Serie 8. 
Se han corregido problemas de estabilidad con algunos sistemas multinúcleo/SMP basados en GPU GeForce 6200/7200/7300. 
Se ha mejorado la función de cambio de pantalla con teclas rápidas en algunos portátiles Lenovo. 
Se ha corregido un problema que se producía en Compiz después de conmutar terminales virtuales. 
Se ha mejorado el rendimiento de RENDER. 
Se ha mejorado la interacción con las pantallas digitales planas Barco y Chi Mei de 56", así como con algunas pantallas planas Gateway de 19". 
Se ha añadido una interfaz para monitorizar la información de estado de PowerMizer. 
Se ha corregido un problema de corrupción del renderizado en el editor de gráficos de Maya. 
Se ha mejorado la interacción entre el modo AFR de SLI y los grupos de intercambio en determinadas GPU Quadro FX. 
Se ha corregido un error que provocaba corrupción de datos al redireccionar XV en GPU sin función TurboCache. 
Se ha mejorado la detección del dispositivo de visualización en las GPU GeForce Serie 8. 
Ahora es más fácil utilizar NVIDIA-settings a resoluciones más bajas, como 1024x768 y 800x600. 
Se ha mejorado la consolidación visual de GLX al utilizar Xinerama con Quadro/GeForce Serie 8 y GPU de generaciones anteriores. 
Se ha añadido soporte experimental para ejecutar X Server con profundidad 30 (10 bits por componente) en las GPU Quadro G8 y posteriores. 
Se ha sorteado un error del kernel/la cadena de herramientas de Linux que provocaba errores de bloqueo (soft lockup) al utilizar la función “suspender” en algunos sistemas Intel.

---

### Post by BiTFx on 2007-12-24
Gracias por la info!!!
 
Saludos

---

