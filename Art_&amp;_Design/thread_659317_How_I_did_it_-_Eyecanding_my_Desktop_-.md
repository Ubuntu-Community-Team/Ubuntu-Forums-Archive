---
title: "How I did it - Eyecanding my Desktop -"
date: 2008-01-05
forum: Art &amp; Design
---

### Post by marcon00 on 2008-01-05
[IMG]http://i71.photobucket.com/albums/i123/marcon00/Screenshot-5.png[/IMG]

[IMG]http://i71.photobucket.com/albums/i123/marcon00/Screenshot-4.png[/IMG]

[IMG]http://i71.photobucket.com/albums/i123/marcon00/Screenshot-3.png[/IMG]

[IMG]http://i71.photobucket.com/albums/i123/marcon00/Screenshot-2.png[/IMG]

[IMG]http://i71.photobucket.com/albums/i123/marcon00/Screenshot-1.png[/IMG]

How I did it all ..


This is my story :

first time i came across Linux was back in 1999, at times of RedHat & Mandrake ( the most user friendly at time)
I tried it many times many versions, but i never had time to acctualy work on any linux properly, because of lack of time or being not that user friendly ! Or even the lack of wide tutorials and different approaches etc... Now i been workin on Ubuntu for exactly 2-3 days,i have to admit that im loving it.. its just crazy ... but to be true, what contributed to my change to Linux is the youtube videos ! and the fact that my friend is having Vista Home Premium edition and well it just keeps crashing and is very unstable not mentioning the Ram Hog it is ... And well i wanted to have all these cool things n GUI the ones everyone is talking about, but i found it so hard to make it all ! i mean all the information is scaterd and takes time to digg it and test it and apply it ! So i figured out, when im done with it all, for future reference i will just type it all, write it down, so i wont forget "How i did it" so next time in case of some misfortunate accident i can follow my own steps in doing it . well my friend saw all the tweaks i did and how stable linux can be .. makin it short.. he is using ubuntu now, and followed mine "HOW i DId it" text file .. and it happened that i already distributed this to couple of people i know ... why not to the whole community ?? maybe at least one of you there will use it :) and find it helpfull !


so this is how my desktop looks after everything basically.. :


Changing the userbar aka taskbar aka menubar aka bar 

Right Click on it Properties, and use an image .. needs a bit of work on any image editing program .. :)

---------------------------------------------------------
Changing splash screen, get them from gnome-look.org

you need to get start Up Manager

[http://web.telia.com/~u88005282/sum/installation.html](http://web.telia.com/~u88005282/sum/installation.html)

---------------------------------------------------------
Do not forget to enable the restricted drivers ...

You want nice 3D effects, Cube effect like seen on youtube Beryl effects and all ? its Compiz-Fusion for YOU !

easy to follow instructions on:
[http://wiki.compiz-fusion.org/Get_Compiz_Fusion](http://wiki.compiz-fusion.org/Get_Compiz_Fusion)

---------------------------------------------------------

Mac Dock ! Avant Window Manager

[http://wiki.awn-project.org/index.php?title=FAQ](http://wiki.awn-project.org/index.php?title=FAQ)

after its all done, sometimes it might happen taht it wont autorun ! so waht u do is type this in console
```

sleep 10 & avant-window-manager
```

---------------------------------------------------------

Icons/Theme .. get them from gnome-look.org

Credit: xiaogray  

simple instructors :

1.install right theme engine
such as gtk-murrine-engine(Murrine GTK2 engine)

u can install them from apt or yum,etc.

2.download themes pkg

3.check if there is a file named 'index.theme' included in this pkg. if not,create it by uself

4.install this pkg(only tar.gz) from Apperence Setting by choosing 'theme>install...' or extract this pkg and put it into /usr/share/themes/ or /home/username/.theme (hidden)

---------------------------------------------------------

FOr 4 Different Wallpapers ! 

credits to : adamruss (compuiz-fusion )	

Ok, This is a small HOW-TO for gnome, if you cant understand it, it's better that you dont do it then, soon nautilus will be patched anyway (gutsy?,suse?)

You Need Wallpaper plugin for this! and you will loose the patched up stuff you'r distro patched in nautilus (there are "nautilus scripts" to replace them though)!

here is how i did it:
got these 2 scripts:
[http://www.russ.co.il/patch/02_compiz_background.patch](http://www.russ.co.il/patch/02_compiz_background.patch)
[http://www.russ.co.il/patch/30_rgba_colormap.patch](http://www.russ.co.il/patch/30_rgba_colormap.patch)

and downloaded eel & nautilus source...
[ftp://ftp.gnome.org/pub/GNOME/sources/nautilus/2.20/nautilus-2.20.0.tar.gz]("ftp://ftp.gnome.org/pub/GNOME/sources/nautilus/2.20/nautilus-2.20.0.tar.gz")

[ftp://ftp.gnome.org/pub/GNOME/sources/eel/2.20/eel-2.20.0.tar.gz]("ftp://ftp.gnome.org/pub/GNOME/sources/eel/2.20/eel-2.20.0.tar.gz")


The following steps will download and reinstall all updates so keep your Ubuntu CD next to ya, i didnt know that at first so preferably disconnect from internet or back your Deb files before and update it from your local folder not from ubuntu archives. Preferable PRINT THIS OUT !!!

logout using CTRL+ALT+Fx (any F1,F2 . key)

THe CODE in the Console .. dont  forget to login as root !
```

sudo -i
/etc/init.d/gdm stop

apt-get remove nautilus
apt-get build-dep nautilus

cd /opt *Replace this with the folder that you downloaded the previous files to*

*if by anychance one of the files werent downloaded properly or you somehow lost it, do not freak out, use wget "insert link here" to downloaded it , and without the quotes.


tar -xvzf nautilus-2.20.0.tar.gz
tar -xvzf eel-2.20.0.tar.gz
mv 02_compiz_background.patch eel-2.20.0
mv 30_rgba_colormap.patch nautilus-2.20.0$ 

cd eel-2.20.0
patch -p1 <02_compiz_background.patch
./configure && make && make install

cd ../nautilus-2.20.0
patch -p1 <30_rgba_colormap.patch
./configure && make && make install

/etc/init.d/gdm start

```

then go to ccsm ( in console or from run *ALT+F2* )
Wallpaper plugin...
if you have Comipz-fusion,and CUbe enabled then simply add wallpapers to yoru cube.

then type in console or run " killall nautilus "  sometimes it restarts, so what i did is CHange option in Sessions ! Under Preferences  then just retyped kill all nautilus as root in the console.

---------------------------------------------------------

 to change icons/themes you can use Gnome Art 

Check the boxes for &#8220;Universe&#8221; and &#8220;Multiverse&#8221; and then hit &#8220;OK&#8221;. Once the additional repositories are enabled, hit the &#8220;Reload&#8221; icon, and then do a &#8220;Search&#8221; for &#8220;Gnome Art&#8221;. Install Art Manager and then close down Synaptic Package Manager

but personally, i checked it all and i havent found anythign really that nice there, but whatever floats your boat mates..

SO any comments are welcomed ;) tell me what u think :P Cheers ~

---

### Post by exneo002 on 2008-01-05
how do I set themes up in ubuntu by the way If you've been working with linux since 1999 you'll know how to dual boot ubuntu ultimate 1.6 [gutsy based and windows] plz dont betray me to a random tutorial I need an actual human explaining how to set up grub and partioning and set up like your upper post so plz I am a new user lookin to dual boot plz help me reply privat me or e-mail me at [email]exneo.socomplayer@yahoo.com[/email]

---

### Post by KimoSaber on 2008-01-05
WOW, looks great. I will try to follow your links. Great job.

---

### Post by adam.tropics on 2008-01-05
@ OP: Very nice, although attaching the pics for thumbnails might have been better!

@exneo002 Just checked your posts. Long day huh.....do you sleep?! You're gonna do better with a separate thread I promise you.

---

### Post by Insomnia777 on 2008-01-06
Heya I must say vewy vewy nice, this all eye candy stuff is really good :D I'll try some things around if I have a question I won't hesitate to do a quiz :P

---

### Post by Insomnia777 on 2008-01-06
Found smth... the Mac Dock ! Avant Window Manager... How can I install it cause it tells me 
it doesn't find the command

---

### Post by Kedster on 2008-01-06
that is my desktop lol i dont have quit as much t if u want all the stuff i can give it to u but i need help how or were could i put a 40.mb file so u can all get it

---

### Post by marcon00 on 2008-01-06
exneo002 , what i ment is that i was trying to ATTEMPT to work on linux since 1999,but i started to work couple days go. So im a begginer, and in two days i managed to do this !If i could do it, you can :) and i showed you how i did it .. so it could help you doing it as well !! :) that is the purpose of this thread ;)

KimoSaber, if you followed it .. tell me how it all turned out ! Im curious if it works the way it worked for me !

adam.tropics , thumbnails ? HoW ?:P

 Insomnia777 , Ints not intsalling because the program is now downloaded n your computer ! i think the website for AWN isnt that clear after all .. i will post it when i come back from university,i just woke up and and i will be late for buss :P Cheers ! tell me more how it went :)

---

### Post by Insomnia777 on 2008-01-06
Kedster how ya got to make the upper bar kinda see through? :P

marc/ ooohhh oki :D... I'll wait then :) ... good luck in college

Thanks ^^

---

### Post by adam.tropics on 2008-01-06
> **marcon00 said:**
> 
adam.tropics , thumbnails ? HoW ?:P

In advanced edit-->attachments (paperclip thingy)!

ps.I remember the RedHat days of 98'-99' you refer to very well! Don't miss them a bit!

---

### Post by JoshuaRL on 2008-01-06
Mine is slightly transparent in Xubuntu.  But I agree, it's sweet.

So Kedster, where did you get that sick background?  That's awesome.

Marcon00, nice thread.  I haven't looked too carefully through your HOWTO, but I'm sure I'll take some of your ideas :P  Isn't it cool to show up brand-new Windows machines with old throwaways?  I sure like it.

---

### Post by Kedster on 2008-01-06
the .deb is for awn just put it on ur hard drive   not on a network then double click it and gbedi will come uppp click install and let it do what it wantss then take go to applications> accessories click on Avant-window_navigator and hopefully it will start if not post the error or what ever 


i dont no were  got it but here it is
 for the panel take the pic and go in to panel properties and then i think backround and use that image sorry i installed kde tonight and i was trying it out so i cant go check but in the morning i can
i forget were i got it ut i got alot of it form here so it might be form here exept the backgounds i found those my self
[here]("http://www.gnome-look.org/content/show.php/..%3A%3AThe+Dark+Theme%3A%3A..?content=66005")

---

### Post by Kedster on 2008-01-06
did the awn work 

ohhh and how do i make pic visible in the post like the guy who started this did i really would rather do that

---

### Post by marcon00 on 2008-01-06
Kedster . simply do this [ img ] link goes here  [ /img ]  and dnt space on the breckets .. :)

Insomnia777 , did u try manual instalaltion of AWN ?? 

wget [https://launchpad.net/awn/0.2/0.2.1/+download/avant-window-navigator-0.2.1.tar](https://launchpad.net/awn/0.2/0.2.1/+download/avant-window-navigator-0.2.1.tar)

and then manual install it ? i didnt use any deb, i dnt use debs often because at least i get proper erro msgs and i can solve things right away :)

---

### Post by JoshuaRL on 2008-01-06
That's cool Kedster, but I was talking about that flame background.  That's sick.

---

### Post by rouge568 on 2008-01-06
The biggest issue with this setup is that there is no window list now that the bottom bar is gone. To fix this, right click on the top bar and select "Add to Panel". Click on "Window List" to apply it. Because this uses a lot of space (depending on the number of open windows), I removed "Menu Bar" and replaced it with "Main Menu". Screenshot attached. There are also a lot of other little fun apps you can add through this menu.

---

### Post by Insomnia777 on 2008-01-06
I set up the AWN bar :D :D :D yey... any themes ye guys can share?  ^^

---

### Post by marcon00 on 2008-01-07
there arent a lot of themes for it :) but you can check in on the main website :)

---

### Post by lonely man on 2008-01-07
> **marcon00 said:**
> 
here is how i did it:
got these 2 scripts:
[http://www.russ.co.il/patch/02_compiz_background.patch](http://www.russ.co.il/patch/02_compiz_background.patch)
[http://www.russ.co.il/patch/30_rgba_colormap.patch](http://www.russ.co.il/patch/30_rgba_colormap.patch)

and downloaded eel & nautilus source...
[ftp://ftp.gnome.org/pub/GNOME/source...-2.20.0.tar.gz](ftp://ftp.gnome.org/pub/GNOME/source...-2.20.0.tar.gz)
[ftp://ftp.gnome.org/pub/GNOME/source...-2.20.0.tar.gz](ftp://ftp.gnome.org/pub/GNOME/source...-2.20.0.tar.gz)



hi...

I can't install 4 desktop wallpapers cuz I can't open this 4 web links

---

### Post by marcon00 on 2008-01-07
my mistake 
[ftp://ftp.gnome.org/pub/GNOME/sources/nautilus/2.20/nautilus-2.20.0.tar.gz]("ftp://ftp.gnome.org/pub/GNOME/sources/nautilus/2.20/nautilus-2.20.0.tar.gz")

[ftp://ftp.gnome.org/pub/GNOME/sources/eel/2.20/eel-2.20.0.tar.gz]("ftp://ftp.gnome.org/pub/GNOME/sources/eel/2.20/eel-2.20.0.tar.gz")

try these :)

---

### Post by lonely man on 2008-01-07
> **marcon00 said:**
> my mistake 
[ftp://ftp.gnome.org/pub/GNOME/sources/nautilus/2.20/nautilus-2.20.0.tar.gz]("ftp://ftp.gnome.org/pub/GNOME/sources/nautilus/2.20/nautilus-2.20.0.tar.gz")

[ftp://ftp.gnome.org/pub/GNOME/sources/eel/2.20/eel-2.20.0.tar.gz]("ftp://ftp.gnome.org/pub/GNOME/sources/eel/2.20/eel-2.20.0.tar.gz")

try these :)

thanks for fast replay...
I downloaded the 2 files that you add... but these links not work also:
[http://www.russ.co.il/patch/02_compiz_background.patch](http://www.russ.co.il/patch/02_compiz_background.patch)
[http://www.russ.co.il/patch/30_rgba_colormap.patch](http://www.russ.co.il/patch/30_rgba_colormap.patch)

if you can kindly please upload them in this forum or send them to my email... if you wish I send my email in private message to you

---

### Post by marcon00 on 2008-01-07
well they do work cuz i personaly tried them . in your console, direct yourself to directory you want the files to be downloaded to.. then type

```

example: cd /home/user/downloads/

and type this within

wget http://www.russ.co.il/patch/02_compiz_background.patch

wget http://www.russ.co.il/patch/30_rgba_colormap.patch

```
you wil have these files within the folder u specified .. :)

---

### Post by Insomnia777 on 2008-01-07
Oops, seems the AWN bar I had on the bottom didn't appear after I restarted... I clicked the AWN Manager and it doesn't work, what can I do about it?

---

### Post by marcon00 on 2008-01-07
AWN manager doesnt work unless you acctauly run AWN , go to Applications - Accessories ! and simply run it ! with me it does not start as well, i tried edditing sessions and add it to start up but with failure ! maybe someone could help ? :)

---

### Post by marcon00 on 2008-01-07
OMG, my Thread hit +1k views, i feel somehow proud ! haha .. anyways, i would like feed back if acctualy this is somehow usefull ! i mean all us n00bs need to support each other too :) i mean, its nice diggin urself for info, but some of us finds it hard :) so comment discuss and tell me what you think !!  .. Cheers ;)

---

### Post by Insomnia777 on 2008-01-07
Well it appeared like this 

```
avant-window-navigator
```

I hit that and I got this :S

```
abner@R2D2:~$ avant-window-navigator
Screen is composited.
LOADED : /home/abner/.config/awn/launchers/awn_launcher.desktop
APPLET : /usr/lib/awn/applets/taskman.desktop

** (avant-window-navigator:6271): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (avant-window-navigator:6271): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (avant-window-navigator:6271): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (avant-window-navigator:6271): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (avant-window-navigator:6271): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (avant-window-navigator:6271): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (avant-window-navigator:6271): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (avant-window-navigator:6271): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 40, in <module>
    import gnomedesktop
  File "/var/lib/python-support/python2.5/gtk-2.0/gnomedesktop/__init__.py", line 1, in <module>
    from _gnomedesktop import *
ImportError: /usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf

```

---

### Post by marcon00 on 2008-01-08
try removing it and remaking it ?  for my n00b head there is something wrong wit the icons ? :P try it .. have you modified anything ? maybe changed some settings ? applied some other unofficial theme ?

---

### Post by lonely man on 2008-01-08
> **marcon00 said:**
> well they do work cuz i personaly tried them . in your console, direct yourself to directory you want the files to be downloaded to.. then type

```

example: cd /home/user/downloads/

and type this within

wget http://www.russ.co.il/patch/02_compiz_background.patch

wget http://www.russ.co.il/patch/30_rgba_colormap.patch

```
you wil have these files within the folder u specified .. :)

thanks again...

I did what you sayed to me, but it's not working also... and this is what in terminal show

```

hussain@Ein:~/wallpaper$ wget http://www.russ.co.il/patch/02_compiz_background.patch
--08:46:59--  http://www.russ.co.il/patch/02_compiz_background.patch
           => `02_compiz_background.patch'
Resolving www.russ.co.il... failed: Name or service not known.
hussain@Ein:~/wallpaper$ wget http://www.russ.co.il/patch/30_rgba_colormap.patch
--08:48:25--  http://www.russ.co.il/patch/30_rgba_colormap.patch
           => `30_rgba_colormap.patch'
Resolving www.russ.co.il... failed: Name or service not known.

```

I'll cry :(

---

### Post by marcon00 on 2008-01-08
Here you go .. :) enjoy 

and i was able to download :) so check ur connections or settings ...

---

### Post by Insomnia777 on 2008-01-08
ok I'll remove it and re-install it

---

### Post by lonely man on 2008-01-08
> **marcon00 said:**
> Here you go .. :) enjoy 

and i was able to download :) so check ur connections or settings ...

hi again dear...

I think you will get mad cuz of me... I did your steps but in another way, and all things go well but I can't but wallpapers to each Desktop...and I'll tell you what I did :
wrote this command at terminal

```
 /etc/init.d/gdm stop 
```

after that I saw the black screen (DOS or Terminal) but I can't write any command... and cuz of this I restart my PC and lunch the OS in recovery mode and did all the steps and every things gos well... but after I restart the PC I could't see any plug-in in CCSM menu or Desktop Cube menu...

soo... what I did is right?

---

### Post by smartboyathome on 2008-01-08
Are you using Compiz Fusion? You must use Compiz Fusion to get multiple wallpapers.

---

### Post by marcon00 on 2008-01-08
YOu are right, it doesnt add a plugin in compiz-fusion ! but when u go to Cube effects just add muliple wallpapers and that is it ! and kill nautilus ! and you will have your 4 wallpapers :)

how to work on 4 wallpapers witout the cube effect ? i dnt know i didnt check, but i guess its going to be under the options of compiz-fusion as well.. just look around and try it .. 

its werid that you couldnt type any commands in the terminal after killing gnome, but still if u aplied all the commands, and it didnt show up with any error, then you should be fine ! so search through cube options and add multiple wallpapers :) tell me how it went...

---

### Post by Insomnia777 on 2008-01-08
sry for the dumb question but... how do I uninstall it? ^^

---

### Post by marcon00 on 2008-01-09
i guess it should to go something like this 

```


sudo apt-get remove appicationnamegoeshere


```

---

### Post by lonely man on 2008-01-09
> **marcon00 said:**
> YOu are right, it doesnt add a plugin in compiz-fusion ! but when u go to Cube effects just add muliple wallpapers and that is it ! and kill nautilus ! and you will have your 4 wallpapers :)

how to work on 4 wallpapers witout the cube effect ? i dnt know i didnt check, but i guess its going to be under the options of compiz-fusion as well.. just look around and try it .. 

its werid that you couldnt type any commands in the terminal after killing gnome, but still if u aplied all the commands, and it didnt show up with any error, then you should be fine ! so search through cube options and add multiple wallpapers :) tell me how it went...

hi...

this my final questions after than I'll never ask...

can you but a screenshot for the location where u can change wallpapers for each Desktop?

cuz I really git confuse ](*,)

---

### Post by MarimaX on 2008-01-09
I could not get a lot of these things to work.  I fear it may be that my video card is old.  it's only 16 mg nvidia geforce2.  Slowly deleting stuff from Dell Insp 9300 in order to dual boot and go from there.

---

### Post by ahm911 on 2008-01-09
I saw that lebanese flag! haha well done bro looks beautifull

---

### Post by smartboyathome on 2008-01-09
> **MarimaX said:**
> I could not get a lot of these things to work.  I fear it may be that my video card is old.  it's only 16 mg nvidia geforce2.  Slowly deleting stuff from Dell Insp 9300 in order to dual boot and go from there.

Is there an entry in System > Preferences called "Advanced Desktop Effects"?

> **lonely man said:**
> hi...

this my final questions after than I'll never ask...

can you but a screenshot for the location where u can change wallpapers for each Desktop?

cuz I really git confuse ](*,)

Same question as above...

---

### Post by MarimaX on 2008-01-10
Yes it is located there... I really believe that its the video card though

---

### Post by lonely man on 2008-01-10
> **smartboyathome said:**
> Is there an entry in System > Preferences called "Advanced Desktop Effects"?



Same question as above...

yes there is... but now I make it on other way but without icons on the Desktop... cuz I open by terminal

**gconf-editor**

and I disable **/apps/nautilus/preferences/show_desktop**

---

### Post by marcon00 on 2008-01-10
lonely man , here you go .. this is the screen shot you requested and please ask as many questions :) we all need to support each other :) 

MarimaX, yeah your 16 Mb is too low for that :) i got 256 Nvidia with 2 GB ram and it slightly , just slightly lags, so imagine.

ahm911 , Lebanese and Proud :P

:)

---

### Post by BobCFC on 2008-01-10
> **marcon00 said:**
> 
its werid that you couldnt type any commands in the terminal after killing gnome, but still if u aplied all the commands, and it didnt show up with any error, then you should be fine ! so search through cube options and add multiple wallpapers :) tell me how it went...


After you stop Gnome it drops you to the messages from the boot.  You need to log in to type commands!  Press Alt-F2 and you will get to a login screen, type in your username and password.

After you have finished the work you can start the desktop again with
```

sudo /etc/init.d/gdm start
```

This is useful for installing graphics drivers etc without rebooting.

---

### Post by smartboyathome on 2008-01-10
BobCFC, you type ctrl+alt+F1-6 for the different virtual terminals.

---

### Post by marcon00 on 2008-01-13
so anything new  mates ? did everythin work out ?

---

### Post by BobCFC on 2008-01-17
> **smartboyathome said:**
> BobCFC, you type ctrl+alt+F1-6 for the different virtual terminals.


Yes, you would if you were already in an X session, but if you kill X and sit at tty1 you can switch between them without the crtl key... like in the old days lol.

---

### Post by gwoodruff on 2008-02-27
Is the wallpaper plugin still needed? I am having problems with installation.

---

### Post by marcon00 on 2008-05-20
Hmmm .. :) neat count of views :P

n no one thanked me ! lol ...

---

### Post by Jabbadahut on 2008-06-03
Man, I always wanted to 'trick out' my desktop.  This looks really wicked,  However I'm not exactly sure if I got it installed correctly as I'm getting an error in the terminal window, as I followed the instructions on [https://help.ubuntu.com/community/CompositeManager/CompizFusion]("https://help.ubuntu.com/community/CompositeManager/CompizFusion").

I seemed to got it to install fine, but I can't seem to run the program.  According to the instructions, to run Compiz, you enter the following command in the Terminal:

```

compiz --replace

```

So this is what I get:

```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 05:00.0 0300: 10de:0402 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.


```

Then it just shows a blinking cursor on the next line, but does not return the 'prompt' - in this case "jabba@lanparty".  So I just closed the terminal.  If I am understanding the error, it sounds like the configuration has a wrong setting, right?  Two things I notice as well...

```
Checking for Xgl: not present.
```

Which is listed twice, whatever it is.

AND

```

/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format,
```

That's Greek to me.  Okay, so how do I fix this whole problem?  Is 'initiate_edge' an editable file or something?  If it is, I can't find it.  I am running 8.04 64-bit version - was this particular software designed only for 32-bit or before the current release?

Thanks in advance to anyone who can lend a helping hand.

 - Jabba

---

### Post by Jabbadahut on 2008-06-04
Does anyone here have an idea on how to resolve this or at least point me in the right direction?

Anyone?  Anyone?

Bueller?  Bueller?

---

