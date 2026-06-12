---
title: "lives not working"
date: 2005-07-25
forum: Absolute Beginner Talk
---

### Post by jasonpeinko on 2005-07-25
Lives wont instal it does not find the GTK 2.0 lib 
and it is installed i looked.

---

### Post by majikstreet on 2005-07-25
what is lives and how are you installing it?
Using a deb file or from source?

---

### Post by claydoh on 2005-07-25
[LiVES]("http://www.xs4all.nl/%7Esalsaman/lives/index.html") is a video editor/Veejay application. Probably trying the deb package found [here.]("http://www.xs4all.nl/%7Esalsaman/lives/downloads.html")
I only had to install python2.3 for it to run (in Kubuntu)

If you are installing from source, then make sure you have the libgtk2.0-dev installed

---

### Post by jasonpeinko on 2005-07-26
[QUOTE=claydoh][LiVES]("http://www.xs4all.nl/%7Esalsaman/lives/index.html") is a video editor/Veejay application. Probably trying the deb package found [here.]("http://www.xs4all.nl/%7Esalsaman/lives/downloads.html")
I only had to install python2.3 for it to run (in Kubuntu)

If you are installing from source, then make sure you have the libgtk2.0-dev installed[/QUOTE]
 ok but i do have libgtk2.0 installed it does the same thing for everything that i have downloaded

---

### Post by claydoh on 2005-07-26
So I assume then you are installing from source?
You need to use synaptic or apt to install libgtk2.0-_***dev***_ as well, and probably a few other xxxx-dev packages as well. These are the parts of the various libraries that are required to compile, but not needed to run an actual binary.

> sudo apt-get install mplayer libgtk2.0-dev libsdl1.2 libsdl1.2-dev libmjpegtools libmjpegtools-dev libjpeg62-dev  
I hope I didn't miss anything.

This should get you everything needed to run LiVES with most functionality.
It is also recommmended to install sox, mencoder, transcode. The only thing that seems to be missing from the repos is libvisual, which is optional anyway.

---

### Post by jasonpeinko on 2005-07-27
[QUOTE=claydoh]So I assume then you are installing from source?
You need to use synaptic or apt to install libgtk2.0-_***dev***_ as well, and probably a few other xxxx-dev packages as well. These are the parts of the various libraries that are required to compile, but not needed to run an actual binary.

 
I hope I didn't miss anything.

This should get you everything needed to run LiVES with most functionality.
It is also recommmended to install sox, mencoder, transcode. The only thing that seems to be missing from the repos is libvisual, which is optional anyway.[/QUOTE]
 when i got into synaptic it says i have GTK installed. i will run the command you told me 2 but i dont have internet yet on my linux comp so i dont know if it will be there

---

### Post by jasonpeinko on 2005-07-27
your commad did not work it could not find mplayer

---

### Post by claydoh on 2005-07-27
You will have to add the other [repositories to your /etc/sources.list]("http://ubuntuguide.org/#extrarepositories") if you have not already done so. You can do it with a text editor, or by using Synaptic.
A correct mplayer version would be mplayer-586, sorry about that.

You will need internet access to get these things.

---

### Post by send4m3 on 2005-07-27
Recently I try for Ubuntu 5.04 LiveCD to try surf in the net, and found firefox browser. How I connect to my ISP then ? 
Please reply also to my email [email]send4m3@yahoo.com[/email], cause I seldom open the forum.
Thanks

---

### Post by jasonpeinko on 2005-07-28
[QUOTE=claydoh]You will have to add the other [repositories to your /etc/sources.list]("http://ubuntuguide.org/#extrarepositories") if you have not already done so. You can do it with a text editor, or by using Synaptic.
A correct mplayer version would be mplayer-586, sorry about that.

You will need internet access to get these things.[/QUOTE]
 ok i dont have internet yet

---

### Post by jasonpeinko on 2005-07-28
[QUOTE=jasonpeinko]ok i dont have internet yet[/QUOTE]
 ok i have internet now (still not wirless :( thouhg)

---

### Post by jasonpeinko on 2005-07-28
[QUOTE=jasonpeinko]ok i have internet now (still not wirless :( thouhg)[/QUOTE]
 there is no MPLAYER in synaptic im just going to download it

---

### Post by jasonpeinko on 2005-07-28
nvm there is no download for linux

---

### Post by claydoh on 2005-07-28
[you need to add to your apt repositories]("http://ubuntuguide.org/#extrarepositories") so you can have access to the software, search for and install mplayer (don't forget to "reload" after adding the new repositories)

---

### Post by jasonpeinko on 2005-07-28
ok i have downloaded programs such as cine and lives and kplayer and when i unpack and run ./configure i always get errors that it cannot find libs and other files and says to check my instalation path. here is now i have it set up.
DESKTOP - DOWNLOADS  downloads is where all my packages are. then i type this:

cd Desktop/DOWNLAODS
tar xvjf kplayer0.5.3.tar.bz2
cd kplayer0.5.3
./configure

---

### Post by jasonpeinko on 2005-07-28
[QUOTE=claydoh][you need to add to your apt repositories]("http://ubuntuguide.org/#extrarepositories") so you can have access to the software, search for and install mplayer (don't forget to "reload" after adding the new repositories)[/QUOTE]
 ok what mplayer do i download
scratch my last message

---

### Post by claydoh on 2005-07-28
[QUOTE=jasonpeinko]ok what mplayer do i download
scratch my last message[/QUOTE]
 mplayer-586 is good, mplayer-386 will work too

---

### Post by jasonpeinko on 2005-07-28
[QUOTE=claydoh]mplayer-586 is good, mplayer-386 will work too[/QUOTE]
 it still says im missing gtk
configure: error: Library requirements (gtk+-2.0 >= 1.3.13) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

---

### Post by claydoh on 2005-07-28
As per my second post :-P

>  You need to use synaptic or apt to install libgtk2.0-_***dev***_ as well, and probably a few other xxxx-dev packages as well. These are the parts of the various libraries that are required to compile, but not needed to run an actual binary. 

libgtk2.0-dev libsdl1.2 libsdl1.2-dev libmjpegtools libmjpegtools-dev libjpeg62-dev  			 		, mencoder, sox, and transcode will need to be installed for a fully functional LiVES.

---

### Post by jasonpeinko on 2005-07-28
[QUOTE=claydoh]As per my second post :-P

 

libgtk2.0-dev libsdl1.2 libsdl1.2-dev libmjpegtools libmjpegtools-dev libjpeg62-dev  			 		, mencoder, sox, and transcode will need to be installed for a fully functional LiVES.[/QUOTE]
 thx so much for your help

---

