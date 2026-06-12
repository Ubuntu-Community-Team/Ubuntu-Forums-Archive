---
title: "[SOLVED] I have a font that ends in .otf"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by steph9700 on 2007-12-20
it is a windows or mac file but has nowhere for me to download it as an Ubuntu user. it is a fingerspelling for sign language font and I am trying to learn American sign language now as I am going deaf. can you please help me figure out what I need to do to install this file on Ubuntu?    [http://www.lapiakdesign.com/fonts.html](http://www.lapiakdesign.com/fonts.html)


(EDIT) I am so green at this my hair and fingertips are green and my toes are growing roots, please explain this to me in the most simple of terms possible, please.

---

### Post by jordanmthomas on 2007-12-20
1.  Download the zip file and save it to your Desktop
2.  Extract the zip file.
3.  Open your home directory in nautilus
4.  Create a folder called .fonts in your home directory (it's ok if you already have one here)
5.  Copy the .otf file(s) into your ~/.fonts directory (you'll need to press ctrl-h to show hidden files)
6.  Open up a terminal
7.  type
```
sudo fc-cache -f
```
to regenerate the font cache and after this, restart any open programs and the font should be available.


This worked fine for me (but I use Archlinux and Ubuntu could potentially be different, although it is unlikely)

---

### Post by steph9700 on 2007-12-20
it didn't work, I EVEN HAD TO RESTART MY COMPUTER USING A BOOT DISK IT SHUT UBUNTU DOWN....:confused:

---

### Post by jordanmthomas on 2007-12-20
Installing a font crashed Ubuntu?
I'm not sure what's wrong on your end, but this worked perfectly here.

---

### Post by jordanmthomas on 2007-12-20
Also, another way you could try is this (though it doesn't always work for me):
1.  Open a nautilus window
2.  Press ctrl - l (that's a lowercase "ell")
3.  type fonts:/// and hit enter.
4.  copy / paste font in here.

---

### Post by steph9700 on 2007-12-20
it didn't crash my system it just wouldn't boot back up properly and I had to reboot in safe mode. I can't copy and paste it because it is hand signs for the letters and numbers not actual letters. if you could I posted the web address of where I got these aslfonts at on the first post, could you go take a look at them then come back and try to help me?

---

### Post by jordanmthomas on 2007-12-20
I looked at these fonts, and I installed them.
I am not sure I know what you mean when you say you can't copy and paste the letters.  You should be able to set the font as Lapiak and use it in any program just like any other font.

Here's the exact commands you would use in a terminal (applications --> accessories --> terminal) to properly install this font after downloading the Windows / Mac version onto your Desktop
```

cd ~/Desktop
unzip  lapiak_asl.zip
mkdir ~/.fonts
cp LapiakASL-Bold.otf ~/.fonts/
cp LapiakASL-Regular.otf ~/.fonts/
sudo fc-cache -f

```

After this, restart any open programs and Lapiak ASL will be an option in its font preferences.  Hope this helps,
The line mkdir ~/.fonts may give you an error saying it already exists.  This is fine, and you should just ignore the error.

---

### Post by steph9700 on 2007-12-20
ok I did that and nothing happened. It must have installed but when I start up my abiword it isn't showing in the list and I looked at every single one. I am so frustrated, I don't know how programmers stay sane. I am just a house wife trying to use what my techy hubby gave me. :(

---

### Post by steph9700 on 2007-12-20
ok this is what I did:


steph@wilemina:~$ 
steph@wilemina:~$ fonts:///
bash: fonts:///: No such file or directory
steph@wilemina:~$ ls
AN00709_.jpg     Desktop                j0323096.jpg    j0426022.jpg  sy00359_.jpg
ATT110967.jpg    Documents           j0323368.jpg    j0434513.jpg  sy00362_.jpg
ATT110971.jpg    dragonheart2.jpg   j0364698.jpg   mask.jpg        sy00675_.jpg
bd10998_.jpg      Examples             j0366822.jpg     Music           sy00678_.jpg
bd11001_.jpg      Fonts                   j0366828.jpg    Pictures         sy01134_.jpg
blackntan_p.jpg   j0322871.jpg        j0368528.jpg    Public             sy01137_.jpg
blackntan_s.jpg   j0322884.jpg        j0368534.jpg    splat_p.jpg      Templates
DD00057_.jpg      j0322893.jpg       j0398579.jpg    splat_s.jpg       Videos
steph@wilemina:~$ cd Desktop
steph@wilemina:~/Desktop$ ls
abiword.desktop   LapiakASL-Bold.otf         pidgin.desktop
firefox.desktop     LapiakASL-Regular.otf     QuickTime731_Leopard.dmg
GALLAUDET.ttf       lapiak_asl.zip                readme.doc
gimp.desktop       my book again.abw        xchat-gnome.desktop
steph@wilemina:~/Desktop$ cd /etc/fonts
steph@wilemina:/etc/fonts$ cp LapiakASL-Regular.otf ~/.fonts/
steph@wilemina:/etc/fonts$ cp LapiakASL-Bold.otf ~/.fonts/
steph@wilemina:/etc/fonts$ sudo fc-cache -f
[sudo] password for steph:
steph@wilemina:/etc/fonts$ exit



and it still didn't install them my hair is turning white and starting to fall out from stress

---

### Post by steph9700 on 2007-12-20
Ok so I did this and didn't see any changes either:


steph@wilemina:~$ cd File System/etc/fonts
bash: cd: File: No such file or directory
steph@wilemina:~$ cd etc/fonts
bash: cd: etc/fonts: No such file or directory
steph@wilemina:~$ cd etc
bash: cd: etc: No such file or directory
steph@wilemina:~$ cd fonts
bash: cd: fonts: No such file or directory
steph@wilemina:~$ cd Desktop
steph@wilemina:~/Desktop$ ls
abiword.desktop  LapiakASL-Bold.otf     pidgin.desktop
firefox.desktop  LapiakASL-Regular.otf  QuickTime731_Leopard.dmg
GALLAUDET.ttf    lapiak_asl.zip         readme.doc
gimp.desktop     my book again.abw      xchat-gnome.desktop
steph@wilemina:~/Desktop$ cp LapiakASL-Bold.otf
cp: missing destination file operand after `LapiakASL-Bold.otf'
Try `cp --help' for more information.
steph@wilemina:~/Desktop$ cp LapiakASL-Bold.otf LapiakASL-Bold.conf
steph@wilemina:~/Desktop$ cp LapiakASL-Regular.otf LapiakASL-Regular.conf

---

### Post by steph9700 on 2007-12-20
ok it changed the name from .otf to .conf but it is still on the desktop, it won't install into my font files so I can use it. I am so tired, I am gonna crash tonight maybe daylight will bring fresh ideas.

---

### Post by jordanmthomas on 2007-12-20
Don't rename them to .conf files.

Maybe tomorrow morning you will reread my posts and they will make more sense to you.  The one where I listed commands should be entered *exactly* as I said.

I am not sure what this is all about?
```
cd File System/etc/fonts
```  ??

What is currently in your .fonts folder?
```
ls -al ~/.fonts
```
What should be in there is those two fonts (.otf)
These shouldn't be in /etc/fonts unless you want them installed for every user on the computer (this is also more complicated to get set up right)

---

### Post by steph9700 on 2007-12-20
I want it in the computer for anyone to use. all of my font files that the ubuntu program installed are in the etc folder in the folder called fonts. as it is they are installed on the desktop and abiweb is not seeing them.

---

### Post by steph9700 on 2007-12-20
steph@wilemina:~$ ls -al ~/.fonts
total 64
drwxr-xr-x  2 steph steph  4096 2007-12-20 01:58 .
drwxr-xr-x 43 steph steph  4096 2007-12-20 09:42 ..
-rw-r--r--  1 steph steph 20996 2007-12-20 02:18 LapiakASL-Bold.otf
-rw-r--r--  1 steph steph 30100 2007-12-20 02:18 LapiakASL-Regular.otf
steph@wilemina:~$ 


this is what is in there right now but my abiword is not seeing the lapiak

---

### Post by steph9700 on 2007-12-20
I can't figure out how to get lapiak installed into whrere it needs to be for abiword and the other wordprocessor to see it and use it, help me in the simplest terms possible as I am not the smartest person in the world!

---

### Post by forestpixie on 2007-12-20
it is in the right place - I did it the same way, so would assume that you have done it correctly - but I have the same problem as you seem to be having and don't know enough to be able to help

when someone can help they will - I expect jordanmthomas will return to help you, in the meantime try to relax :)

---

### Post by steph9700 on 2007-12-20
O.K. I have gotten to this:

[email]steph@wilemina:/etc/fonts/conf.avai[/email]l$ 


How do I install ---- 
LapiakASL-Bold.otf  ----  AND ----   LapiakASL-Regular.otf


into that file? I tried:
[COLOR="DarkGreen"] [email]steph@wilemina:/etc/fonts/conf.avai[/email]l$ install LapiakAsl-Bold.otf
and it said this:
steph@wilemina:~/Desktop$ ls
abiword.desktop  LapiakASL-Bold.conf     my book again.abw
firefox.desktop  LapiakASL-Bold.otf      pidgin.desktop
GALLAUDET.ttf    LapiakASL-Regular.conf  xchat-gnome.desktop
gimp.desktop     LapiakASL-Regular.otf
steph@wilemina:~/Desktop$ install LapiakASL-Bold.conf
install: missing destination file operand after `LapiakASL-Bold.conf'
Try `install --help' for more information.[/COLOR]
[COLOR="Indigo"]

steph@wilemina:~/Desktop$ cd ~
steph@wilemina:~$ cd root
bash: cd: root: No such file or directory
steph@wilemina:~$ cd etc
bash: cd: etc: No such file or directory
steph@wilemina:~$ cd ./etc
bash: cd: ./etc: No such file or directory
steph@wilemina:~$ 
Display all 1990 possibilities? (y or n)
steph@wilemina:~$ ~./etc
bash: ~./etc: No such file or directory
steph@wilemina:~$ cd /etc/fonts/conf.avail
[email]steph@wilemina:/etc/fonts/conf.avai[/email]l$ instll /etc/fonts/LapiakASL-Regular.otf
bash: instll: command not found
[email]steph@wilemina:/etc/fonts/conf.avai[/email]l$ install /etc/fonts/LapiakASL-Regular.otf
install: missing destination file operand after `/etc/fonts/LapiakASL-Regular.otf'
Try `install --help' for more information.
[email]steph@wilemina:/etc/fonts/conf.avai[/email]l$ /etc/fonts/LapiakASL-Bold.otf
bash: /etc/fonts/LapiakASL-Bold.otf: Permission denied
[email]steph@wilemina:/etc/fonts/conf.avai[/email]l$ [/COLOR]


[COLOR="DarkRed"]I am just not getting it I guess, all this typing in a little box makes no sense to me, I am not understanding what letter or command or whatever I need to put the damn file where it needs to be for the whole effin computer to use.[/COLOR]

---

### Post by steph9700 on 2007-12-20
and I am so sorry I am getting so testy. I have no patience and I have used up what little control I have and I don't mean to take it out on yall. :neutral::-#:cry::frown:

---

### Post by thelatinist on 2007-12-20
I am pretty sure AbiWord doesn't support .otf fonts.  Neither does OpenOffice.  Both are treating this not as a bug, but as a feature request which seems not to be getting top priority.  This is a shame, since most of the major font producers have converted over all their libraries to OpenType.

Linux itself should be able to handle the fonts through fontconfig, and they should be available in Gedit and some other applications.  Check to see if these fonts are available in Gedit; if they are, then they are properly installed but they won't be available to you in AbiWord.

A workaround is to convert the fonts to .ttf using FontForge.  You will lose some of the special features of OpenType (ligatures, special kerning, etc.) but you should be able to use them in AbiWord and OpenOffice.org.

---

### Post by steph9700 on 2007-12-20
I tried to do that gedit and it didn't recognize the file. I have changed them from .otf to .conf using the little terminal box and when I click on the file name on the desktop it comes up it is just not going into my font files for abiword to use it. It is a free font for me to use and on my first post I gave the link to the page. How do I fix the file so it will go in and be able to be used by the fonts file for abiword and the other word processor?

---

### Post by thelatinist on 2007-12-20
> **steph9700 said:**
> I tried to do that gedit and it didn't recognize the file. I have changed them from .otf to .conf using the little terminal box and when I click on the file name on the desktop it comes up it is just not going into my font files for abiword to use it. It is a free font for me to use and on my first post I gave the link to the page. How do I fix the file so it will go in and be able to be used by the fonts file for abiword and the other word processor?

Wait, you should not have changed the names of the fonts.  Leave them as .otf.

Also...the font should not be on your desktop.  You should have copied it either to /usr/share/fonts/truetype/myfonts or to a folder named .fonts in your home folder.  In post # 14 it appeared that you had already done that...

You also should not be trying to open the fonts with Gedit.  Gedit is a text editor.  What I said was to see if the fonds are available to  _use_ in Gedit.  To do that just:

1) Open gedit
2) Edit > Preferences > Font & Colors
3) Uncheck "Use the system fixed width font."
4) Click "Editor Font" and see if your font is in the resulting dialog.

If it is there, then the font is properly installed.  As I said, I don't think AbiWord or OpenOffice *can* use .otf fonts at all...this is just to confirm that they are properly installed.  If AbiWord still can't see it, that's because it (still) doesn't have OpenType font support, and you won't be able to get it to work in AbiWord.  If that's the case, the only work-around would be to convert it to ttf.

---

### Post by forestpixie on 2007-12-20
that should work for you fine in there steph9700 - they are available for me in gedit to use - to change the font in there go to edit - preferences, fonts and colours and untick the system font box

---

### Post by steph9700 on 2007-12-20
I tried this which my husband did last night and I am not sure what it means but it won't install that way either but here it is:


[sudo] password for steph:
root@wilemina:~# install /home/steph/Desktop/LapiakASL-Bold.conf ~/etc/fonts/conf.avail
install: cannot create regular file `/root/etc/fonts/conf.avail': No such file or directory
root@wilemina:~# apt-get install lapiakASL-Bold.conf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package lapiakASL-Bold.conf
root@wilemina:~# apt-get install lapiakASL-Bold.otf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package lapiakASL-Bold.otf
root@wilemina:~# 




Ok I opened that applications/graphics/gimp image editor and it is installed in there but I don't know how to use it. I want this font in abiword, how do I do that one supposedly simple thing?

---

### Post by forestpixie on 2007-12-20
ok - it works in kword, so as long as you have no problem installing kde apps on a gnome system that should be you sorted.

You can install it through add/remove or synaptic, but quickest way is with the terminal 

```
sudo apt-get install kword
```

once you've installed it - check the font is there for you, if it's not gop back to the beginning and follow jordan's thread on how to install the font

---

### Post by steph9700 on 2007-12-20
the thing that is in the applications/accessories/text editor is what your talking about right? I did that and it is there. Thank you
I just want it in abiword too:(

---

### Post by thelatinist on 2007-12-20
> **steph9700 said:**
> Ok I opened that applications/graphics/gimp image editor and it is installed in there but I don't know how to use it. I want this font in abiword, how do I do that one supposedly simple thing?

As I have already said twice, you can't.  AbiWord doesn't use .otf fonts.  It doesn't have the ability.  That you can access the fonts in the gimp just confirms this.

If you want to use these fonts, you will have to convert them to ordinary TrueType fonts (.ttf) using FontForge.  Install it from the repositories, open your .otf files, and then choose File > Generate Fonts.  In the resulting dialog box, where it says PS Type 1 (Binary) change it to say TrueType.  Then click save.  Install the resulting fonts as you did the otf ones.

I have done this for you and attached the files below, tarred and gzipped.

---

### Post by steph9700 on 2007-12-20
ok I got kword and it is in it. thank you, I just hate trying to learn a new word processor to use my font. I guess I am lucky to have it at all so thank you guys very much for putting up with me!:)

---

### Post by thelatinist on 2007-12-20
> **steph9700 said:**
> ok I got kword and it is in it. thank you, I just hate trying to learn a new word processor to use my font. I guess I am lucky to have it at all so thank you guys very much for putting up with me!:)

Install the converted fonts, above, and you should be able to use them in AbiWord.

---

### Post by forestpixie on 2007-12-20
> the thing that is in the applications/accessories/text editor is what your talking about right

no kword is a different app - but you should be ok now with thelatinist's timely help

can you make sure you mark thread once you're happy

---

### Post by steph9700 on 2007-12-20
ok I downloaded the zip file and it is on my desktop, what do I do now? forgive me, I am very new to computers in general. also how do I mark thread when I feel done?

---

### Post by thelatinist on 2007-12-20
> **steph9700 said:**
> ok I downloaded the zip file and it is on my desktop, what do I do now? forgive me, I am very new to computers in general. also how do I mark thread when I feel done?

Double-click it, and it should open up your default archiving program.  Use it to extract the files to either /usr/share/fonts/truetype/myfonts or to the folder named .fonts in your home folder.

---

### Post by forestpixie on 2007-12-20
click thread tools and there's a mark thread solved button

---

