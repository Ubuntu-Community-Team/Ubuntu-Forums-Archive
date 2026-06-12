---
title: "newbie needs some help with ubuntu ( or linux in general ) :)"
date: 2005-05-13
forum: Absolute Beginner Talk
---

### Post by hiptrop on 2005-05-13
hi i am pretty new to linux and expecially new to ubuntu :) so far i really like it !

but here are some questions i cannot figure out!

first of all i have installed opera ... works fine ... but i have to start it in the shell !

is there a way that i can make a symbol like firefox ? ( or any other program i have installed  ? ) 


next : 
the package thing with ubuntu really does work great but i keep on getting an errors ...

checking for jpeg_start_decompress in -ljpeg... no
configure: error: jpeg library not found

configure: error: glut.h version is too old.

and the last one for now ... i am not sure if i got the newest drivers for my ati 9700  mobile card installed ... at least there is one game that i have installed
 ( armagetronad ) which does not look to complex but runs really slow ( 14 fps with minimum resolution and no graphic effects ! ) 

ps: if anybody can tell me how i can use the tv out port with linux that would be really nice too :) 

pss: i don't know why but the site [www.ati.com](www.ati.com) is down for 2 days ... do you have the same experience ? 

well for solong i guess these are more than enough questions ! i hope you can help me out and i want to thank you for any help :)

---

### Post by bored2k on 2005-05-13
- For the opera shortcut: if you are using gnome, check out [http://www.realistanew.com/projects/smeg/](http://www.realistanew.com/projects/smeg/) .

- [http://ubuntuforums.org/showthread.php?t=24557&highlight=ati+driver](http://ubuntuforums.org/showthread.php?t=24557&highlight=ati+driver) (the squeamish should look away on this one) .

---

### Post by hiptrop on 2005-05-13
thanks for the fast help :) 

for the other problems i would be very thankfull too :) 

:)

---

### Post by harryc on 2005-05-13
What are you trying to install and how?

> next :
the package thing with ubuntu really does work great but i keep on getting an errors ...

checking for jpeg_start_decompress in -ljpeg... no
configure: error: jpeg library not found

configure: error: glut.h version is too old.

---

### Post by hiptrop on 2005-05-13
gracer and xracer !

on both i getthese 2 different errors !

i just do a ./configure command as root !

---

### Post by bored2k on 2005-05-13
[QUOTE=hiptrop]gracer and xracer !

on both i getthese 2 different errors !

i just do a ./configure command as root ![/QUOTE]
 APT ["ubuntu package thing"] has nothing to do with things you do through ./configure..

Just do sudo apt-get install xracer tuxracer inside a terminal window.

---

### Post by poofyhairguy on 2005-05-13
[QUOTE=hiptrop]gracer and xracer !

on both i getthese 2 different errors !

i just do a ./configure command as root ![/QUOTE]

Install your programs in synaptic. Be sure to enable the universe.

[http://www.ubuntulinux.org/wiki/HowToAccessTheUniverseRepository/view?searchterm=universe](http://www.ubuntulinux.org/wiki/HowToAccessTheUniverseRepository/view?searchterm=universe)

---

### Post by hiptrop on 2005-05-13
[QUOTE=bored2k]APT ["ubuntu package thing"] has nothing to do with things you do through ./configure..

Just do sudo apt-get install xracer tuxracer inside a terminal window.[/QUOTE]

ok thanks alot guys ! 
although i do not really understand what the problem is !( why is it a problem when i download the source and compile it myself ? )


 ( xracer worked with graphic bugs and a framerate of 3 fps ( guess 3d acceleration is not activated :P ) 

guess i will have a second look concerning the ati driver :)

gracer was not found with synaptic ( does not matter ... ) just playing around with ubuntu :) 

but there is another problem i have encountert .. 

trying to watch a dvd and it is stutters all the time :( 
does anybody know what the problem could be ? 

got winxp installed too and there it is no problem ! 

thanks alot for the fast help ! you are really great ! :)

---

### Post by harryc on 2005-05-13
For the stuttering DVD, try to enable DMA on your CDROM.

[http://www.ubuntuforums.org/showthread.php?t=28788&highlight=enable+dma](http://www.ubuntuforums.org/showthread.php?t=28788&highlight=enable+dma)

---

### Post by poofyhairguy on 2005-05-13
[QUOTE=hiptrop]
trying to watch a dvd and it is stutters all the time :( 
does anybody know what the problem could be ? 
[/QUOTE]

Yes. DMA isn't turned on. Look at this thread:

[http://www.ubuntuforums.org/showthread.php?t=30949&highlight=dma](http://www.ubuntuforums.org/showthread.php?t=30949&highlight=dma)

---

### Post by somuchfortheafter on 2005-05-13
also for some good reading for the background knowledge you need check out ubuntuguide.org

---

### Post by hiptrop on 2005-05-14
mhmhm as far as i can see .... i have dma enabled ! 

:P

mhmhm i will try another dvd but that kind of sucks :(

---

### Post by hiptrop on 2005-05-14
[QUOTE=somuchfortheafter]also for some good reading for the background knowledge you need check out ubuntuguide.org[/QUOTE]

thanks :)

---

### Post by harryc on 2005-05-14
[QUOTE=hiptrop]mhmhm as far as i can see .... i have dma enabled ! 

:P

mhmhm i will try another dvd but that kind of sucks :([/QUOTE]That would be odd since it's usually off by default. You are running this command right?

```
sudo hdparm -v /dev/hdc
```

Please post the results of it here.

---

### Post by hiptrop on 2005-05-14
ok you seem to be right ! 

but ! : 

with : 

sudo gedit /etc/hdparm.conf

i get :

#/dev/discs/disc0/disc {
#	mult_sect_io = 16
#	write_cache = off
#	spindown_time = 240
#}

#/dev/discs/disc1/disc {
#	mult_sect_io = 32
#	spindown_time = 36
#	write_cache = off
#}

[COLOR=Red]#/dev/cdroms/cdrom0 {
#	dma = on		[/COLOR]   
#	interrupt_unmask = on
#	io32_support = 0
#}

with your command :

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
root@taff3:/home/taff3 #

so i guess it is not activated ! :P

---

### Post by hiptrop on 2005-05-14
have activated it now ! :) 

thanks for reasking ! thought the .conf file tells me the dma settings !

---

### Post by harryc on 2005-05-14
Add the following lines underneath all the text with the hash marks (##):

```


command_line {

    hdparm -d1 /dev/hdc 

}
```


Make sure to leave a blank space at the bottom of the page.

Save the hdparm.conf file and reboot. Check the DMA setting, it should now be active for HDC.

"ok you seem to be right" - You are joking right? :).

---

### Post by TravisNewman on 2005-05-14
hiptrop: One thing to keep in mind-- most every config file, if there's a line with a hash mark (#) at the beginning, that line is commented out, so it won't actually read that part. If it's commented out, it isn't on at all. But it's better to add that part that was suggested a couple posts up.

---

### Post by hiptrop on 2005-05-14
[QUOTE=harryc]Add the following lines underneath all the text with the hash marks (##):

```


command_line {

    hdparm -d1 /dev/hdc 

}
```


Make sure to leave a blank space at the bottom of the page.

Save the hdparm.conf file and reboot. Check the DMA setting, it should now be active for HDC.

"ok you seem to be right" - You are joking right? :).[/QUOTE]

hehe sorry :) did not mean to be disrespectiful :)   not at all :) 

which file do you mean ? i mean where do i have to add those command lines ? 

and does anybody know what the glut.h error while configuring gracer means ?
just downloaded the newest glut.h file and replaced it with it ! ( hope i am allowed to do this ... but i guess i am :P ) 

still does not work :( 

thanks alot guys ! really awesome what you are doing here !

---

### Post by hiptrop on 2005-05-14
ok i figured it out :) 

edited the hdparm.conf file of course :) 

i edited it to : 

command_line {

    hdparm -d1 -c3 /dev/hdc 

(c3 for 32 bit support ! ) 

/dev/hdc:
 IO_support   =  3 (32-bit w/sync)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

any body know what the last error means ? 

thanks alot all :)

---

### Post by harryc on 2005-05-14
I don't think it's a meaningful error, I get the same thing.  I'd ignore it.

---

### Post by Stormy Eyes on 2005-05-14
[QUOTE=hiptrop]HDIO_GETGEO failed: Invalid argument

any body know what the last error means ? 

thanks alot all :)[/QUOTE]

hdparm is just being stupid; it's trying to determine your drive's capacity, but since your DVD-ROM doesn't necessarily have media mounted, that operation fails. You can safely ignore it.

---

