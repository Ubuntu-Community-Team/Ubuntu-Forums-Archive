---
title: "Acer 3680 con Atheros, GMA 950 y orbicam SOLUCION"
date: 2007-12-29
forum: Argentina Team
---

### Post by Duyos on 2007-12-29
Buenas. 
Para todos aquellos que estan luchando con una acer 3680 o similar con wireless atheros.
En ocasion de pasarme a linux probe mas de 7 distribuciones hasta encontrar la que mejor le sentaba a mi acer y a mi modo de trabajar. 
Si bien Mandriva es una opcion muy interesante y una de las que mas me gusto, la facilidad y docilidad de los paquetes dev, del sudo, del aptitude, etc
hicieron que volviera a Ubuntu que de todas sus versiones es la que mas me gusta.
Bien, a los hechos.
 
VIDEO
en la version Gutsy la gma 950 esta soportada
de todas maneras siempre se puede hacer lo siguiente:

	sudo aptitude update && sudo aptitude install 915resolution

SONIDO
Abrir Control de Volumen
	Si no sabes donde escontrarlo abri la grabadora de sonido y buscalo en archivo.
	Siempre te conviene entrar en la configuracion para poder mostrarlo en aplicaciones. 
En el control de volumen activas sorrownd y ya te funcionan los parlantitos
si enchufas los auriculares igual siguen funcionando, de manera que si queres hacer exclusivo los auriculares tenes que volver
a silenciar el sorround

CAMARA ORBICAM

hay de todo por la web, pero sin tocar nada con el amsn la camara funciona de 10, 
y como es una camara medio pelo no creo que la quieras para muchas mas cosas que para eso, no probe con programas de grabacion
pero calculo que funciona 

WIRELESS ATHEROS
 Esto es lo mas dificil de todo, porque hay muchas recetas
y casi todas te orientan hacia el mismo final
pero  en [http://techaspect.net](http://techaspect.net) encontre la posta posta.

1. Download the ndiswrapper (v1.49 source code and AR5007EG Windows drivers:

wget [http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.49.tar.gz?modtime=1193538074&big_mirror=0](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.49.tar.gz?modtime=1193538074&big_mirror=0)

2. Download the AR5007EG Windows XP drivers:
If you’re using a 32-bit version of Linux, use this command:

wget [http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz)

If you’re using a 64-bit version of Linux, use this command:

wget [http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz)

2. Extract the archives (change them to suite your file names):

tar xvf ar5007eg-*.tar.gz
tar xvf ndiswrapper-newest.tar.gz

3. Ensure you have your kernel headers and the build essential package.

sudo apt-get update && sudo apt-get install linux-headers-$(uname -r) build-essential

4. Blacklist the ath_pci kernel module (it doesn’t support our chipset).

echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist

5. Compile ndiswrapper (change them to suite your file names) :

pushd ndiswrapper-*/ar5007eg-* (Use Nautilus to find the file)
sudo ndiswrapper -i net5211.inf
popd

7. Make sure ndiswrapper loads up every time we start Linux:

sudo modprobe ndiswrapper
echo "ndiswrapper" | sudo tee -a /etc/modules

8. Restart your computer.

sudo init 6

---

### Post by User21 on 2007-12-29
Fantastico aporte! :)

---

