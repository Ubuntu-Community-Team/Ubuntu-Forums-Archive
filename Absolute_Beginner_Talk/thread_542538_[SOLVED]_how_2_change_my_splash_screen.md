---
title: "[SOLVED] how 2 change my splash screen??"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by shortybookit on 2007-09-04
should be simple enough

---

### Post by dreadlord_chris on 2007-09-04
> **shortybookit said:**
> should be simple enough
more or less.... simple, that is....
depending on which spalsh screen you're refering too - and you should probably tell which window manager/desktop environment you're using....

---

### Post by shortybookit on 2007-09-04
just a general question so any splash screen?
isnt there a place to change it ilke u can change backgroun,window login,screen saver?

i am on 7.04

---

### Post by Golyadkin on 2007-09-04
It depends on which splashscreen you want to change for example:  the usplash screen which shows up while you boot (the Ubuntu / Kubuntu) or the splash screen of Gnome when you start the window manager... tell us which you want to change and we can try to help.

---

### Post by nowshining on 2007-09-04
or you can turn it all the way off note that if the splashscreen is TOO SMALL OR TOO BIG your session into your desktop WILL crash..

---

### Post by dptxp on 2007-09-04
sudo apt-get install gnome-splashscreen-manager

Then go to system>preferences>splash screen to make changes.

---

### Post by ramjet_1953 on 2007-09-04
If you want to go one step further, install [COLOR="Blue"]gnome-art[/COLOR]

[COLOR="Red"]sudo apt-get install gnome-art[/COLOR]

It includes splash screen editor and heaps more.

Regards,
Roger 8)

---

### Post by shortybookit on 2007-09-04
thank you much to the last 2 posts

but i keep getting an error when i am in the terminal

this is what it says

E: Type '*' is not known on line 38 of source list /etc/apt/sources.list
E: the list of sources could not be read

when i go to that file i do not get code for anything i get a few tabs to choose from and a few boxs to tick 

no line 38 to edit 

so now what?

---

### Post by shortybookit on 2007-09-04
anyone?

---

### Post by Obor on 2007-09-04
can you post content of your /etc/apt/sources.list by going to the terminal and
```
gedit /etc/apt/sources.list
```

If you wanna fix it yourself you can make a backup and open it as root by: (you will be able to save changes you make. don't recommend this unless you know what you doing):
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
gksudo gedit /etc/apt/sources.list 
```

---

### Post by svalding on 2007-09-04
try updating your list with 

```
 sudo apt-get update 
```

Correct me if I'm wrong on that command fellas, but I think that is the one that allows you to update the source list.

---

### Post by shortybookit on 2007-09-04
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


# compiz-fusion by Treviño's Ubuntu feisty EyeCandy Repository

    * ## Avant Window Navigator
    * deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) edgy avant-window-navigator
    * deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) edgy avant-window-navigator

---

### Post by shortybookit on 2007-09-04
get the same error when i try to update my list

---

### Post by shortybookit on 2007-09-04
it works now i took out the bottom few lines of code since this was all i added but now back to the original problem the knome art manager 

now it says it could not find package knobe art

---

### Post by Obor on 2007-09-04
yep, thats exactly what you should do (lines that are commented out should start with #)

The package name is **gnome-art**

---

### Post by shortybookit on 2007-09-04
it cant find the package

---

### Post by WebSiteGuru on 2007-09-04
> **Golyadkin said:**
> the usplash screen which shows up while you boot (the Ubuntu / Kubuntu) or the splash screen of Gnome when you start the window manager...

How do you change that one?

---

### Post by WebSiteGuru on 2007-09-04
Why did you have * at the last 3 rows? I dont think that is correct. Change it to #.


> **shortybookit said:**
> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


# compiz-fusion by Treviño's Ubuntu feisty EyeCandy Repository

    * ## Avant Window Navigator
    * deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) edgy avant-window-navigator
    * deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) edgy avant-window-navigator

---

### Post by shortybookit on 2007-09-04
its not correct!!! i said i took those lines out but it still is not working

---

### Post by Obor on 2007-09-04
> **shortybookit said:**
> it cant find the package

Your sources list is a bit of a mess. Are you using Feisty? What are all the dapper repos there for?
You dont have universe and multiverse repo in your list (you have disabled dapper ones there)

If you are using Feisty the you should add this to your sources list:
```

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

```

and then update with
```
sudo apt-get update
```
After that you should have the gnome-art available.
In normal circumstances you should edit your sources list using the Software sources  item in the Admin menu. That way you would avoid having messy/broken sorces list.

---

### Post by mlentink on 2007-09-04
change the first two lines in your sources.lst
```
deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
```
to 
```
deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
```

and try again

I don;t know off the top of my head which repo those packages are in

---

### Post by WebSiteGuru on 2007-09-04
Is it the same errors? or different one after you took it out?

---

### Post by shortybookit on 2007-09-04
dude this freakin ubuntu crap is pissingf me off

why the hell cant you just click on something and it works????

now i am tring to edit the source list 

i open it edit it but fregin save is not an option what the hell

gedit /etc/apt/sources.list is what i used to open it

---

### Post by shortybookit on 2007-09-04
after changing the top to lines and adding the code the other guy said my new source.list file looks like this

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

when i tried to 
get install gnome-splashscreen-manager i got this error
E could not open lock file var/lib/dpkg/lock-- open 13 per,missions denied
E unable to lock the administration directory var/lib/dpkg,are you root?

i am root i am the only user how do i change my permissions and what permissions do i have to change/

---

### Post by WebSiteGuru on 2007-09-04
That **read only mode**

> **shortybookit said:**
> gedit /etc/apt/sources.list is what i used to open it

You'll have to do this. put sudo in front of it.

```
sudo gedit /etc/apt/sources.list
```

You'll have to put in your password.

---

### Post by shortybookit on 2007-09-04
ok i did that and it installed then my update maneger came up and there was 10 updates which i installed so if i want to install this [http://gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468](http://gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468)

how do i do it

---

### Post by WebSiteGuru on 2007-09-04
Did you installed splashscreen manager? See quote below for instruction. > **dptxp said:**
> sudo apt-get install gnome-splashscreen-manager

Then go to system>preferences>splash screen to make changes.

---

### Post by shortybookit on 2007-09-04
i have an art manager but no splash screen manager
when i go in to the art manager i can change my splash screen but there are like 100 pre defined ones and no option to install or add one

---

### Post by shortybookit on 2007-09-04
hey website guru

could you go check out this post as well i have been asking this q for days in different forums and i didnt get an answer yet

thanks in advance
[http://ubuntuforums.org/showthread.php?t=542565](http://ubuntuforums.org/showthread.php?t=542565)

---

### Post by WebSiteGuru on 2007-09-04
Was this problem solved? if yes, mark it as [SOLVED] with the thread tools.

---

### Post by WebSiteGuru on 2007-09-04
> **shortybookit said:**
> hey website guru

could you go check out this post as well i have been asking this q for days in different forums and i didnt get an answer yet

thanks in advance
[http://ubuntuforums.org/showthread.php?t=542565](http://ubuntuforums.org/showthread.php?t=542565)

K I will.

---

### Post by shortybookit on 2007-09-04
no it has not been solved i am still were i left off

here is a copy and paste of my last msg

i have an art manager but no splash screen manager
when i go in to the art manager i can change my splash screen but there are like 100 pre defined ones and no option to install or add one

---

