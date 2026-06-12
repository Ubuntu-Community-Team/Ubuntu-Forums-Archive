---
title: "Can't install Dangerdeep"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by Smaug067 on 2006-11-25
OK... I've read almost every thread regarding permissions, installation, etc. When attempting to run the .bin installer for Dangerdeep, I get a message box "This installer requires root privileges. Please become superuser before executing the installer." I've used the sudo su command (under terminal) and still get the same error message. Just about ready to hurl a brick thru the monitor.:???:

---

### Post by junglepeanut on 2006-11-25
[http://www.dangerdeep.net/documentation.php](http://www.dangerdeep.net/documentation.php)

Compiling on Unix and Linux

To compile Danger from the Deep, you will need the SDL, SDL-image, FFTW3 and optionally the SDL-net and SDL-mixer libraries and their corresponding development packages.

Extract the files using the following command (substitute the name of the file instead of <file.tar.gz>): tar -zxf <file.tar.gz>

From version 0.0.18 onwards we use the SCons build system. To build the game, change into the dangerdeep directory and type the following commands:

scons (will build the binary, also with mingw under Windows)
scons install (as root, will install the game, only with Linux or Unix, only version 0.0.19 and newer)

To run the game, type dangerdeep. To run Danger from the Deep in a different resolution or in windowed mode, see the Command-line Options section below.

Just wondering what happened when you tried this stuff? From their site

---

### Post by Smaug067 on 2006-11-25
> Just wondering what happened when you tried this stuff?

I haven't tried any of this, just downloaded the [Linux Installer]("http://prdownloads.sourceforge.net/dangerdeep/dangerdeep-0.2.0-linux-installer.bin?download") and double-clicked on the .bin file. Will give this a try. Thanks!

---

### Post by Smaug067 on 2006-11-27
OK, I got the game to install, but whenever I try to drag the "data" file to the "dangerdeep" file under "games", I get a permissions error. I have tried:

sudo -i
sudo -s
sudo su
sudo -h

all to no avail. This morning I edited my login settings to allow me to logon as an administrator, but had to leave for work. I will try it this evening and post an update.

---

### Post by junglepeanut on 2006-11-27
Thanks if you can not get it figured out, I will give it a go. But the holiday period is over so I am back at school so responses will not be as quick as before...maybe somebody else will beat me to it. :)

---

### Post by Smaug067 on 2006-11-27
WOOOO-HOOOO!!!!!:mrgreen: I used the terminal to mv the .bin installer to my root desktop, logged out, logged in as root, ran the installer, and I am off hunting me some battleships!;) The graphics are excellent as far as I cakn tell. Now I'm off to find an appropriate driver for my archaic 3Dfx Voodoo2 graphics accelerator (I know it's on the net somewhere):p

---

### Post by junglepeanut on 2006-11-29
Sounds good, hopefully you don't need to always run root.

---

