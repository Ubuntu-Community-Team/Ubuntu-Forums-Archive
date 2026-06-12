---
title: "Just a few questions"
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by Sp@z on 2005-12-14
HI I am very new to Linux and Ubuntu 5.10 period. I have a few questions that I am not exactly looking for answers to ...........yet.........I will make seperate posts if they are not wasting time.

I am doing this because I have made a few posts and not gotten ALOT of help although ppl have tried. And I really don't want to waste anyones time.

1) Webpages using Windows media player 10 that stream music and videos, Firefox tells me I need a plug in and directs me to Windows media player 10 websight. I know it isn't going to install............Should I give up on that and "Get over it?"

2)My dvd player doesn't suppport DMA, it is OLD but runs perfect in Windows 98 SE, very choppy in Linux................Will it ever work under linux since my DVD doesn't support DMA?

3)I am a gamer and when and if I load linux on my desktop, will I be able to install games such as Quake4, Unreal Tournament 2004and Unreal Tournament 99 on it? And will it play as good as it does in windows?

I am sure there are more questions that some I can find on my own by experimenting...and I will.........

I condider myself very lucky to have only these issues, but I am hoping to get rid of windows completly on my Laptop and my desktop. I guess there is another question in itself..........

4) Is it even feasible to think someone can totally get rid of windows and be a PURE Linux user?

5) can someone clear up for me what the terminolgy is for my DVD rom drive that is posted in my Siggy? I swear I think it is PMCMIA, but I would like to get the igornace out of my siggy! LOL

Thank you and I am asking these questions so I can LEARN what is possible and what isn't possible to be able to streamline my thoughts and hopes for Linux..........

Thanx in advance for your help. :)

---

### Post by endersshadow on 2005-12-14
1. sudo apt-get install mozilla-mplayer
2. Probably will be choppy due to libdvdcss being, well, not exactly legal and therefore very little help from DVD.
3. [Cedega](http://www.transgaming.com/)
4. I am.
5. [http://www.pcmcia.org/](http://www.pcmcia.org/)

---

### Post by Estariel on 2005-12-14
> 
 1) Webpages using Windows media player 10 that stream music and videos, Firefox tells me I need a plug in and directs me to Windows media player 10 websight. I know it isn't going to install............Should I give up on that and "Get over it?"


get the media player kaffeine (it is in synaptic). It has a plugin called kaffeine-mozilla (or something, not sure about the name). Maybe the plugin must be selected in synaptic as well, I don't remember (Maybe it just gets installed with kaffeine).

Then install the w32codecs (restricted formats in the ubuntu wiki). If you search the forums for this, you will find lots of how - tos.
This will give you .wma and .wmv support.

Now the streaming media will work in 80% of all cases. I haven't been able to figure out why the last 20% just won't work, but maybe the w32codecs don't support the very latest .wma and .wmv....

> 
 2)My dvd player doesn't suppport DMA, it is OLD but runs perfect in Windows 98 SE, very choppy in Linux................Will it ever work under linux since my DVD doesn't support DMA?
 

No idea about this one, but since it works with win98 it should run on ubuntu as well...

> 
 3)I am a gamer and when and if I load linux on my desktop, will I be able to install games such as Quake4, Unreal Tournament 2004and Unreal Tournament 99 on it? And will it play as good as it does in windows?


You are lucky because you are only asking for games that indeed have been ported to linux (thank you SO much, id Software and Eidos!)
You can buy the linux versions here: tuxgames.com
Or if you own the windows version, you can download the linux binaries here: icculus.org

UT2004 has a linux installer on its DVD.

As for games without a native linux port, most of them don't work.
You have to use a runtime environment for these, like cedega ([www.transgaming.com)](www.transgaming.com)). They have a compatibility database.

The only game I own, that works perfectly with cedega is Warcraft3.

> 
 4) Is it even feasible to think someone can totally get rid of windows and be a PURE Linux user?

Yes, no problem at all.
I got rid of all of windows 5 years ago, and I am doing all my research (physics PhD student), writing, listening to music, etc. etc. on linux.

When you get confortable around linux, you will see that most things are even a lot more easy on linux than on windows...

> 
 5) can someone clear up for me what the terminolgy is for my DVD rom drive that is posted in my Siggy? I swear I think it is PMCMIA, but I would like to get the igornace out of my siggy! LOL


No idea about this one, sorry

Hope I could help
Estariel

---

### Post by endersshadow on 2005-12-14
[QUOTE=Estariel]get the media player kaffeine (it is in synaptic). It has a plugin called kaffeine-mozilla (or something, not sure about the name). Maybe the plugin must be selected in synaptic as well, I don't remember (Maybe it just gets installed with kaffeine).[/QUOTE]
He's using Ubuntu, not Kubuntu.  Get mozilla-mplayer, NOT kaffeine.

---

### Post by Perfect Storm on 2005-12-14
Some information you may want to take a closer look upon:
[http://help.ubuntu.com/starterguide/C/](http://help.ubuntu.com/starterguide/C/)
[http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)

---

### Post by Estariel on 2005-12-14
[QUOTE=endersshadow]He's using Ubuntu, not Kubuntu.  Get mozilla-mplayer, NOT kaffeine.[/QUOTE]

I think that xine handles wmv streams a lot better than mplayer (disclaimer: I don't have any facts for this, this is just personal experience..), and suggested kaffeine because of that.
But maybe there is a mozilla-xine package.. (never checked...)

---

### Post by gil-galad on 2005-12-14
mozilla-mplayer is fantastic.

---

### Post by Gustav on 2005-12-14
And if using Xine in gnome, go with totem-xine

---

### Post by Sp@z on 2005-12-14
Thank you for all your replies and help. I am desperatley trying to reslve these issues and so far it is working. I have the Mozilla mplayer installed and it still doesn't work. But since I know these things will work I will continue to look for answers thank you very much.

---

### Post by NotJustANewbie on 2005-12-14
Mozilla-mplayer didn't work for me either.

---

### Post by endersshadow on 2005-12-14
[QUOTE=Sp@z]Thank you for all your replies and help. I am desperatley trying to reslve these issues and so far it is working. I have the Mozilla mplayer installed and it still doesn't work. But since I know these things will work I will continue to look for answers thank you very much.[/QUOTE]

```
sudo apt-get install mplayer-386 mplayer-fonts mozilla-mplayer
sudo mv -f /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.a /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.a_backup
sudo mv -f /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.la /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.la_backup
sudo mv -f /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.so /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.so_backup
sudo mv -f /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.xpt /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.xpt_backup
```

Execute those commands in the terminal, restart Firefox, and you should be all set.

---

### Post by Sp@z on 2005-12-14
mplayer-fonts is already the newest version.
mozilla-mplayer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.
root@Ubuntu:/home/bill # sudo mv -f /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.a /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.a_backup
mv: cannot stat `/usr/lib/mozilla-firefox/plugins/libtotem_mozilla.a': No such file or directory
root@Ubuntu:/home/bill # sudo mv -f /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.a /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.a_backup
mv: cannot stat `/usr/lib/mozilla-firefox/plugins/libtotem_mozilla.a': No such file or directory
root@Ubuntu:/home/bill # sudo mv -f /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.la /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.la_backup
mv: cannot stat `/usr/lib/mozilla-firefox/plugins/libtotem_mozilla.la': No such file or directory
root@Ubuntu:/home/bill # sudo mv -f /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.so /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.so_backup
mv: cannot stat `/usr/lib/mozilla-firefox/plugins/libtotem_mozilla.so': No such file or directory
root@Ubuntu:/home/bill # sudo mv -f /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.xpt /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.xpt_backup
mv: cannot stat `/usr/lib/mozilla-firefox/plugins/libtotem_mozilla.xpt': No such file or directory
root@Ubuntu:/home/bill #


I get alot of this when I run commands. I wonder if I have a bad install? I know these things should be there but alas they are not. :( thank you for trying though.

---

### Post by endersshadow on 2005-12-14
Just a question...why are you running as root and doing sudo commands?

---

### Post by Sp@z on 2005-12-14
I thought I was supposed too:confused: I just know my friend told me anytime I use the console to log in as root.

---

### Post by endersshadow on 2005-12-14
[QUOTE=Sp@z]I thought I was supposed too:confused: I just know my friend told me anytime I use the console to log in as root.[/QUOTE]

You're friend is giving bad advice. Heh.

You aren't logging into GNOME as root, are you?  Like, at the login screen?

Operate in the console as your normal user.  If you need superuser permissions, use sudo.  If you need to do a bunch of stuff as root, su into root.  *Always make sure to log out of root!*  That is important.  Also, after you're done with the sudo commands, run

```
sudo -k
```

To kill the sudo permissions.

For right now, though, what's in your /usr/lib/mozilla-firefox/plugins directory?

---

### Post by Sp@z on 2005-12-14
essential-20050412
essential-20050412.tar.bz2
flashplayer.xpt
libflashplayer.so
libjavaplugin.so
mplayerplug-in.so
mplayerplug-in.xpt
mplayerplug-in-gmp.so
mplayerplug-in-gmp.xpt
mplayerplug-in-qt.so
mplayerplug-in-qt.xpt
mplayerplug-in-rm.so
mplayerplug-in-rm.xpt
mplayerplug-in-wmp.so
mplayerplug-in-wmp.xpt
nppdf.so

there are the contents of my plug in folder. I am no longer logging in as root and no I was not logging in from the login screen as root :)
I wonder if it has anything to do with the tar file that is in there?

Thanx for your help in this..................

oh yeah, the same friend reccomended Unbuntu Breezy to me, although I love it (Other than all the brown *GAG*) is there a better/easier version out there? Maybe a lil more compatible with my old computer?

---

### Post by Sp@z on 2005-12-17
bump the mplayer issue it is still nagging me. :)

---

### Post by Third Thoughts on 2005-12-17
Have you installed the w32 codecs yet. That random tar file you have (essential...), those are the codecs, but you might not have extracted them to the right place. It looks you might have just extracted it into your firefox plugins folder. I extracted them to /usr/lib/w32, which I where I believe mplayer looks for them. Try re-extracting from the tar file to that location. 

~Andrew S.

---

### Post by Sp@z on 2005-12-18
Thank you for the reply, I am having issues wit tar files and extraction. If some one wants to post here a lil howto I would appreciate it. I googled it and I must not know the correct terminology since I am getting wierd returns.
Thank you. I am also going to great another post and hopefully get some help in another thread.

---

### Post by bscbrit on 2005-12-18
Have a look at 

'man tar'

on a command line (without the quotes).  It's heavy going at first but try the examples and it will fall into place.  Press q to exit from man pages.


ps yours is not an avatar that can be ignored.....

---

### Post by Sp@z on 2005-12-18
Thank you for the help, the avatar is from my girlfriend and she thinks it fits me so well! She calls me the "Deathmetal dad" LMAO.

---

### Post by bscbrit on 2005-12-18
And 


info tar

actually has a tutorial for the tar command.

---

