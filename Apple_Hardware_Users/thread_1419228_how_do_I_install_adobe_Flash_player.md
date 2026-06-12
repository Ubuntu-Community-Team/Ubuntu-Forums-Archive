---
title: "how do I install adobe Flash player"
date: 2010-03-01
forum: Apple Hardware Users
---

### Post by jazzlukejosh on 2010-03-01
Can any one help?
I've been following this tutorial on how to install Adobe flash player but as usual, they talk like you already know what your doing, unfortunatel I don't. This is what they have said to do so far:

First you need to edit the /etc/apt/sources.list [[COLOR=#3333ff][COLOR=#3333FF ! important][FONT=Verdana][COLOR=#3333FF ! important][FONT=Verdana]file[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.debianadmin.com/how-to-install-adobe-flash-in-debian-etchlennysid.html#") using the following command

nano /etc/apt/sources.list    


add the following line:

deb [http://www.backports.org/debian](http://www.backports.org/debian) etch-backports main contrib non-free
  
Done that

save and exit the file. Update the source list using the following command:
#apt-get update

Done that

All backports are deactivated by default. If you want to install something from backports run:


#apt-get -t etch-backports install “packagename”


I tried to this and got this message:

 Couldn't find package “packagename”

I'm assuming I should write the name of the package I want to install inbetween the quote marks

How do I find out what the name of the packakage I want to install is??

If there an esier way to install Adobe flash player, I'd love to hear it??

[INDENT]





[/INDENT]

---

### Post by mickie.kext on 2010-03-01
Umm... I don't think there is Flash Player for PowerPC. You can try Gnash of SWFdec, I think that both are in Software center. It emulate Flash 8 so it might not work for all sites, but is better than nothing.

---

### Post by linuxopjemac on 2010-03-02
[http://mac.linux.be/content/watching-youtube-and-lack-flash](http://mac.linux.be/content/watching-youtube-and-lack-flash)

---

### Post by migel_wimtore on 2010-03-02
I'v had allot of trouble getting flash videos to work on my ppc g4 ibook. Youtube isnt a problem, simply install the firefox add-on greasemonkey and run this script: 

[http://userscripts.org/scripts/show/50771](http://userscripts.org/scripts/show/50771) 

Thanks to Megaloler for that link. 
Oh, and i needed to have vlc installed before greasemonkey would handle youtube. 
As for other flash videos, mplayer sometimes steps in and streams for me, but usually i have to use a flash video downloader through firefox and watch them in vlc from my desktop.

Would love to know i there is a more comprehensive solution for handling online flash videos.

Edit: Ps: there is no adobe flash player for powerpc linux, hence all the work arounds. Good luck.

---

