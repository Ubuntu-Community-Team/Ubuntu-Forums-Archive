---
title: "[SOLVED] New Setup with Ubuntu 7.10 dual booting with WinXP Pro SP2...Now I have ques"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by bconverse on 2007-10-24
Hi Everyone,

I have a number of questions regarding Ubuntu 7.10 and the overall setup of my PC.  I consider myself to be an above average computer user, at least in regards to Windows, but when it comes to Ubuntu, I have absolutely not idea what is going on.  I was able to complete the dual boot install, but now I need some help and guidance.  I've been looking around trying to read up on some of this stuff, but I tend to understand things better if someone gives me a personal rundown. 

 So, my first question involves the boot loader.  Before I installed Ubuntu, I was dual booting WinXP Pro and Windows Vista.  After a few months of using Vista, I noticed that I was never really using it (probably because I didn't like it).  So, I deleted that partition.  Ubuntu was then installed in the free space I had left on my hard drive where Vista used to be.  For some reason in the GRUB bootloader, I get all the Ubuntu options, but, Windows is listed as Vista/Longhorn.  When you select it, however, it runs my WinXP.  So, is there a deeper problem here, or should I be able to change the entry title to Windows XP?  Also in regards to GRUB, I want to make the boot timeout longer than 10 sec, and (for now) WinXP as the default.  I am assuming all three of these tasks can be done in the same place, I just have no idea where...So any help would be appreciated.

My next question is in regards to media files.  I have a 500GB hard drive with all of my music, movies, tv shows, ect. on it.  It is formatted in NTFS, as I was using Windows.  Do I need to do anything special to this drive to have access to the media files in Ubuntu? Can they be accessed anyways despite the formatting? I also have a few folders on the Windows XP partition that I would like be able to access every now and then from Ubuntu (My Documents specifically) and I guess the same sort of access question applies to them.  

Ok, two software related questions.  I know there is tons of stuff in regards to this subject, but again, I often prefer personal opinions.  I am looking for a good media player,  I am a Winamp user, so I suppose something comparable, but, I am trying new things, so I am open to anything.  The only thing that bothers me about most media players is they tend to sort your files without you asking them to.  I have my music sorted in a way that I like, and Winamp keeps the directory structure in the library.  Is there a program that does this in Ubuntu?  Next, I currently use GB-PVR in Windows as a media center.  Is there a "media center" type program for Ubuntu?  I use my computer as my TV in my apartment, so this is pretty important to me.


OK, whew, that was more long winded than I hoped.  Hopefully all of this makes sense.

Thanks again for any help!

---

### Post by blackaardvark on 2007-10-24
Well you can change the name on the GRUB by typing this in the terminal (found in accessories)

```
sudo gedit boot/grub/menu.lst
```



and just changing the name near the bottom where it says Vista. Ur timeout length can be altered there too *I think*

Beyond that, I'm guessing gutsy can read ntfs as easily as feisty can so it should work from the get go.

Exaile (GNOME) or Amarok (KDE) are decent media players with plug-ins etc. but I don't know about the whole arrangement problem.

Oh and MythTV is rather media centre-ish. I havent used it though..

---

### Post by Darzic on 2007-10-24
in the same place as you can change the name and time.  you will see the default option being set to 0

0 being ubuntu

since your xp partition should be the 5th choice, you will have to change that 0 to a 4  (5 choices starting at 0  is the reason for using number 4)   now you should always boot from xp as default

---

### Post by P4man on 2007-10-24
In addition to what was said above: the reason you see "XP/Vista" is because the Vista bootloader is probably still used. First grub would boot, then if you select the windows option, it will load Vista's bootloader which you probably haven't removed. This bootloader will then boot XP. YOu can change this, but it could be a bit of a pain, so I wouldn't touch it yet for now. If the vista bootloader defaults to the vista installation that is no longer there, there is a program here that can help you out:
[http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home](http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home)

As for an alternative to winamp.. try winamp :D.

Seriously, it runs fine under Ubuntu using Wine (windows compatibility layer). Just install wine first (add remove programs). Then open a terminal and type "winecfg" once to launch a wine configuration tool. You shouldnt have to change much if anything there, just close it.  then download winamp installation, and run it!

---

### Post by bconverse on 2007-10-24
Thanks for the suggestions! I am at work now, so I will try all of this stuff out when I get home.  




> **P4man said:**
> In addition to what was said above: the reason you see "XP/Vista" is because the Vista bootloader is probably still used. First grub would boot, then if you select the windows option, it will load Vista's bootloader which you probably haven't removed. This bootloader will then boot XP. YOu can change this, but it could be a bit of a pain, so I wouldn't touch it yet for now. If the vista bootloader defaults to the vista installation that is no longer there, there is a program here that can help you out:
[http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home](http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home)

As for an alternative to winamp.. try winamp :D.

Seriously, it runs fine under Ubuntu using Wine (windows compatibility layer). Just install wine first (add remove programs). Then open a terminal and type "winecfg" once to launch a wine configuration tool. You shouldnt have to change much if anything there, just close it.  then download winamp installation, and run it!

In regards to this, Initially after I uninstalled Vista, the Vista bootloader was still appearing at startup, with the option for windows xp or vista.  I figured out how to get rid of that bootloader, so it would just start xp automatically at startup.  So, prior to installing Ubuntu, the Vista bootloader had been deleted.  Which is why I don't understand why the Windows entry in GRUB is Vista/Longhorn, when the only Windows installation I have is XP. Anways, I guess I'll just rename it to XP for now, just to appease myself, I am sure whatever problem is underneath this is nothing urgent, as I can both boot fine, its just a nomenclature thing.

---

### Post by P4man on 2007-10-24
Im guessing Vista left some "marks" somewhere anyway that grub picked up. On one machine I have the same thing actually, I never noticed earlier, and it did have Vista once, before I removed it and replaced it with XP (using XP bootloader). Grub also shows longhorn/vista for some odd reason

My main machine had only XP before I added Ubuntu, and in that grub menu it shows quite correctly shows "Windows XP Media Center Edition".

---

### Post by bconverse on 2007-10-24
OK, I got home from work a little while ago, and I've been toying with Ubuntu.  I am trying to edit the menu.lst file, however, every time I try and save it, it tells me I can't save it. I don't know if I am entering something wrong?  This makes me feel like quit the n00b.

---

### Post by logos34 on 2007-10-24
You need to open it as root:

gksudo gedit /boot/grub/menu.lst

---

### Post by blackaardvark on 2007-10-24
gksudo... i was so close!

---

### Post by jaybombalous on 2007-10-24
sudo works just as well. gksudo is a graphical interface equivalant. I am not really sure beyond that if there is a difference. I find using gksudo more tedious then just using sudo from terminal.

I believe if u use gksudo u don't lock up the terminal for future use before closing the program u opened with sudo, but I am not exactly sure. More clarification from someone who knows more would more beneficial, I am sure of this.

---

### Post by logos34 on 2007-10-24
> **blackaardvark said:**
> gksudo... i was so close!

well, sudo will work too, it's just that gksudo is preferred way.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by jaybombalous on 2007-10-24
audacious is also the best media player I have found that does exactly what I want without all the ********, its like what winamp was 5 - 6 years ago. A awesome media player minus the ********.

---

### Post by jaybombalous on 2007-10-24
> **logos34 said:**
> well, sudo will work too, it's just that gksudo is preferred way.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

ok so fine, I understand a little now, but why make it so tedious to use. wish u could keybind the gksudo command. I use ubuntu because I like how easy it is to use as a linux distro. Why the need to make it harder then it has to be?

---

### Post by logos34 on 2007-10-24
yeah, audacious is great little player...my fav

as far as sudo/gksudo, I just err on the side of caution.  What's two extra letters?

---

### Post by jaybombalous on 2007-10-25
its not just two extra letters. First u need to open a terminal, type 'gksudo' wait for it to pop up with the graphical interface enter your command and then it opens the file.

I mean, as long as I got the terminal open then why not just use it to type out the whole command using sudo? 

Isn't it possible to type out the whole command in the terminal without the graphical interface poping up asking me to type in the command again?

---

### Post by jaybombalous on 2007-10-25
OK nvm, you are right, its just two letters. I wasn't aware that u could type gksudo and the rest of the command at one time, I should have known better.

---

### Post by logos34 on 2007-10-25
the only drawback of having to open graphical apps from the terminal is that it ties up that particular terminal window until you close it.  So to avoid that you can do:

**ALT+F2** (opens **Run Application** dialog box, where you enter 'gksudo...')

Or use a terminal based editor like **vi **or **nano** (easier) to edit system config 
files

ex:
**sudo nano -w** /boot/grub/menu.lst

---

