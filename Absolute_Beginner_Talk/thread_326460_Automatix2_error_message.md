---
title: "Automatix2 error message"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by Pinon on 2006-12-27
**Problem using Automatix2**

While using Automatix2 for installing plug-ins, most programs gives this error message: "E:Type 'wget' is not known in line 52 in the source liste etc/apt/sources.list, E:The list of sources could not be read."

Is there someone who knows what can be done to fix this problem? 

Thank you :-)

---

### Post by taurus on 2006-12-27
Paste your /etc/apt/sources.list here then!!!

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by jonathan.lees on 2006-12-27
You could make sure that wget is installed. Open a terminal and type:

which wget

If it's installed it should respond /usr/bin/wget

If no reponse, you can install wget with:

sudo apt-get install wget

---

### Post by Pinon on 2006-12-27
Thank you!

I have tried all of the posted help, but I still get the same error message.

The command: which wget
gave result: /usr/bin/wget


What is the next I should try?

---

### Post by jonathan.lees on 2006-12-27
> E:Type 'wget' is not known in line 52 in the source liste etc/apt/sources.list, 

There seems to be a misconfiguration in the sources.list file. Open a terminal and type:

cat /etc/apt/sources.list

Copy the output and paste it here

---

### Post by Pinon on 2006-12-27
Oh, PASTE the list you said...

Here goes the pasted list...

johnny@johnny-laptop:~$ cat /etc/apt/sources.list

deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

#AUTOMATIX REPOS START

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse
#AUTOMATIX REPOS END
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C
sudo apt-key add -
sudo apt-get update
sudo apt-get install automatix2
johnny@johnny-laptop:~$

---

### Post by jonathan.lees on 2006-12-27
Remove the following lines:

> wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C
sudo apt-key add -
sudo apt-get update
sudo apt-get install automatix2

You can do this by typing:

sudo pico /etc/apt/sources.list

scroll down to the lines and remove them with the delete key. When your finished press CTRL+O to save and CTRL+X to exit and then try automatix again.

---

### Post by Pinon on 2006-12-27
Thank you,  the command made this output:

"deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy universe"

What shall i do then?

---

### Post by taurus on 2006-12-27
> **Pinon said:**
> Thank you,  the command made this output:

"deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy universe"

What shall i do then?

You have an entry **"** at the beginning and an extra **"** at the end.  Remove them both or at least the one at the beginning of it...

---

### Post by Pinon on 2006-12-27
Sorry, I am new to all of this.

The lines i have to move, did you mean the lines:

"deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy main restricted"


And the line:

"# deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy universe"

Thank you!

---

### Post by taurus on 2006-12-27
Do you see the " in front of deb at the begining?  It shouldn't be there!!!  

```

**[COLOR="Red"]"[/COLOR]**deb http://no.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://no.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://no.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://no.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://no.archive.ubuntu.com/ubuntu/ edgy universe"

```

---

### Post by Pinon on 2006-12-27
The quote-sign was misplaced in the text be me. It was not in the code.

Now there is this error message: "Error: Broken Count > 0"

What can I do?

Beside this, the "Settin up an Running Script"-screen reports of an conflict between skype and sun-java5-bin. The screen is in norwegian so i might have to translate the best I can, if you need that information.

Any idea of what can be done? 

Thank you :)

---

### Post by taurus on 2006-12-27
What is the exact error message when you run this command from a terminal?

```
sudo aptitude update
```
Also, can I have a look at your /etc/apt/sources.list again, entirely?

```
cat /etc/apt/sources.list
```

---

### Post by Pinon on 2006-12-27
Thank you again for your kind help :)

Her comes some codes..

johnny@johnny-laptop:~$ sudo aptitude update
Password:
Leser pakkelister ... Ferdig
Skaper oversikt over avhengighetsforhold       
Reading state information ... Ferdig    
Initializing package states ... Ferdig
Building tag database ... Ferdig      
Get:1 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/main Translation-nb                       
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/restricted Translation-nb                 
Get:2 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]         
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Translation-nb          
Ign [http://dl.google.com](http://dl.google.com) stable Release.gpg                                     
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-nb                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-nb                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-nb                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-nb                    
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-nb                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-nb          
Get:5 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates Release.gpg [191B]              
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release                      
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/main Translation-nb               
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/restricted Translation-nb         
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-nb                         
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy Release                                   
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-nb               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-nb         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-nb           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-nb
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-nb              
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates Release                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-nb            
Hit [http://dl.google.com](http://dl.google.com) stable Release                                         
Hit [http://dl.google.com](http://dl.google.com) stable/non-free Packages                               
Get:8 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]    
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-nb     
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-nb     
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-nb
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-nb
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-nb
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-nb
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release                             
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages                
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/main Packages                             
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                    
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/restricted Packages                       
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/main Sources            
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/restricted Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages    
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/main Packages                     
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/restricted Packages               
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/main Sources                      
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/restricted Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages
Fetched 9B in 1s (9B/s)
Leser pakkelister ... Ferdig
johnny@johnny-laptop:~$ cat /etc/apt/sources.list
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

#AUTOMATIX REPOS START

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse
#AUTOMATIX REPOS END
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
johnny@johnny-laptop:~$

---

### Post by taurus on 2006-12-27
Well, the output of "sudo aptitude update" looks to be normal to me.  Now, run

```
gksudo automatix2
```
(since you have been waiting for hours to get automatix2 running...  ;) )

---

### Post by Pinon on 2006-12-27
I preciate your help and patientness!!   :-D 

The Automatix2's Error and information-screen says: 
   "An apt-based error occured and inst. was unsuccessful".

The red "ball"(?) at the top of the screen informs: "Broken Count > 0."


Im confused, lucky me, I can ask you!

---

### Post by taurus on 2006-12-27
And lucky me, I get to answer it!  :twisted: 

Try to remove and install it again.

```
sudo aptitude remove automatix2
sudo aptitude update
sudo aptitude install automatix2
```
Now, there should be an icon in Applications -> System Tools.  Click on that and see what happens...

---

### Post by Pinon on 2006-12-27
Noooo.

Well, my problem seems to be your problem. After Bill is gone, you will still have plenty of codes to fix!

Fun? At leat you will be employed. 

What to dooo? Are you not giving up on me yet?

---

### Post by taurus on 2006-12-27
What is the exactly error message and which command did you run to get that error message?

p.s.  Who's Bill?

---

### Post by Pinon on 2006-12-27
Did you mean the Automatix2: Error and Information Report?
It says:
FATAL ERROR: Flash Player
An apt-based error occured and installation was unsuccessful.

By the way. Don't worry about that Bill.

PS! I m not quit sure if my system managed to remove the Automatix, the Terminal-codes are still in a open terminal window if you want more endless codes to read. But it is like good reading, isn't it??

---

### Post by taurus on 2006-12-27
Did you run the automatix2 from Applications -> System Tools or did you run it from a terminal?  To make sure you really remove it before you install it again, try

```
sudo aptitude --purge automatix2
sudo aptitude update
sudo aptitude install automatix2
```
Applications -> System Tools -> Automatix.

---

### Post by Pinon on 2006-12-27
This happend after sudo aptitude...

sudo aptitude --purge automatix2
Password:
Unknown command "automatix2"
aptitude 0.4.1

Looks to me it failed because of the statement Unknown command "automatix2".

Or did it go right?? Shall I just type the next command??

---

### Post by taurus on 2006-12-27
Oh dear, I think I need a long break...

```

sudo aptitude --purge remove automatix2
sudo aptitude update
sudo aptitude install automatix2

```

---

### Post by Pinon on 2006-12-27
I have only typed the first line.

and i ALREADY have a question for you (lucky you!!)

Should i care about the last statement:
   E: Couldn't lock list directory..are you root?


Or what about
   Do you want to continue? [Y/n/?] y
Writing extended state information ... Feil  (Feil [norwegian] means ERROR)


Oh pherhaps i am giving in, the clock is 02:19 AM here.  ](*,) 


Have a nice working day (or night) !!!

---

### Post by Pinon on 2006-12-28
I tried to run this codes....

sudo aptitude --purge remove automatix2
sudo aptitude update
sudo aptitude install automatix2


Here are the results from the terminal...


johnny@johnny-laptop:~$ sudo aptitude --purge remove automatix2
Password:
Leser pakkelister ... Ferdig
Skaper oversikt over avhengighetsforhold       
Reading state information ... Ferdig    
Reading extended state information       
Initializing package states ... Ferdig
Building tag database ... Ferdig      
The following packages are BROKEN:
  skype 
The following packages have been automatically kept back:
  linux-image-2.6.17-10-generic linux-restricted-modules-2.6.17-10-generic 
  linux-restricted-modules-common 
The following packages have been kept back:
  avahi-daemon capplets-data evince gdm gimp gimp-data gimp-python 
  gnome-control-center gnome-games gnome-games-data gnome-system-tools 
  gnupg info language-pack-en language-pack-gnome-en libavahi-client3 
  libavahi-common-data libavahi-common3 libavahi-core4 libavahi-glib1 
  libgimp2.0 libgnome-window-settings1 libgnomeprintui2.2-0 
  libgnomeprintui2.2-common libgnomevfs2-0 libgnomevfs2-bin 
  libgnomevfs2-common libgnomevfs2-extra libgsf-1-114 libgsf-1-common 
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libmagick9 
  libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-data-tds1.0-cil 
  libmono-security1.0-cil libmono-sharpzip0.84-cil libmono-sqlite1.0-cil 
  libmono-system-data1.0-cil libmono-system-web1.0-cil 
  libmono-system1.0-cil libmono0 libmono1.0-cil libpng12-0 
  linux-headers-2.6.17-10 linux-headers-2.6.17-10-generic mono-common 
  mono-gac mono-jit mono-runtime openoffice.org openoffice.org-base 
  openoffice.org-calc openoffice.org-common openoffice.org-core 
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome 
  openoffice.org-gtk openoffice.org-impress openoffice.org-java-common 
  openoffice.org-math openoffice.org-style-default 
  openoffice.org-style-industrial openoffice.org-writer python-uno screen 
  sun-java5-bin tar ttf-opensymbol vino x11-common xbase-clients xorg 
  xserver-xorg xserver-xorg-input-all xserver-xorg-video-all xutils 
The following packages will be REMOVED:
  automatix2 
0 packages upgraded, 0 newly installed, 1 to remove and 83 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
[COLOR="Red"]The following packages have unmet dependencies:
  skype: Avhenger av: libqt3-mt but it is not installable or
                      libqt3c102-mt (>= 3:3.3.3.2) which is a virtual package.
Resolving dependencies...
E: Klarte ikke å finne en fil for pakken sun-java5-bin. Det kan bety at du må ordne pakken selv (fordi arkitekturen mangler).[/COLOR]
The following actions will resolve these dependencies:

Install the following packages:
libqt3-mt [3:3.3.6-3ubuntu3 (edgy, edgy)]

Score is -19

Accept this solution? [Y/n/q/?] y
The following packages have been automatically kept back:
  linux-image-2.6.17-10-generic linux-restricted-modules-2.6.17-10-generic 
  linux-restricted-modules-common 
The following NEW packages will be automatically installed:
  libqt3-mt 
The following packages have been kept back:
  avahi-daemon capplets-data evince gdm gimp gimp-data gimp-python 
  gnome-control-center gnome-games gnome-games-data gnome-system-tools 
  gnupg info language-pack-en language-pack-gnome-en libavahi-client3 
  libavahi-common-data libavahi-common3 libavahi-core4 libavahi-glib1 
  libgimp2.0 libgnome-window-settings1 libgnomeprintui2.2-0 
  libgnomeprintui2.2-common libgnomevfs2-0 libgnomevfs2-bin 
  libgnomevfs2-common libgnomevfs2-extra libgsf-1-114 libgsf-1-common 
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libmagick9 
  libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-data-tds1.0-cil 
  libmono-security1.0-cil libmono-sharpzip0.84-cil libmono-sqlite1.0-cil 
  libmono-system-data1.0-cil libmono-system-web1.0-cil 
  libmono-system1.0-cil libmono0 libmono1.0-cil libpng12-0 
  linux-headers-2.6.17-10 linux-headers-2.6.17-10-generic mono-common 
  mono-gac mono-jit mono-runtime openoffice.org openoffice.org-base 
  openoffice.org-calc openoffice.org-common openoffice.org-core 
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome 
  openoffice.org-gtk openoffice.org-impress openoffice.org-java-common 
  openoffice.org-math openoffice.org-style-default 
  openoffice.org-style-industrial openoffice.org-writer python-uno screen 
  sun-java5-bin tar ttf-opensymbol vino x11-common xbase-clients xorg 
  xserver-xorg xserver-xorg-input-all xserver-xorg-video-all xutils 
The following NEW packages will be installed:
  libqt3-mt 
The following packages will be REMOVED:
  automatix2 
0 packages upgraded, 1 newly installed, 1 to remove and 83 not upgraded.
Need to get 0B of archives. After unpacking 8921kB will be used.
Do you want to continue? [Y/n/?] y
[COLOR="Red"]Writing extended state information ... Feil
E: Klarte ikke å finne en fil for pakken sun-java5-bin. Det kan bety at du må ordne pakken selv (fordi arkitekturen mangler).
E: Couldn't lock list directory..are you root?[/COLOR]
johnny@johnny-laptop:~$ 
johnny@johnny-laptop:~$ 
johnny@johnny-laptop:~$ sudo aptitude update
Leser pakkelister ... Ferdig
Skaper oversikt over avhengighetsforhold       
Reading state information ... Ferdig    
Reading extended state information       
Initializing package states ... Ferdig
Building tag database ... Ferdig      
Get:1 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/main Translation-nb                       
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/restricted Translation-nb                 
Ign [http://dl.google.com](http://dl.google.com) stable Release.gpg                                     
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-nb                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-nb                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-nb                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-nb                    
Get:3 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates Release.gpg [191B]              
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/main Translation-nb               
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/restricted Translation-nb         
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-nb                         
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-nb                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-nb          
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy Release                                   
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                            
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-nb                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-nb          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-nb            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-nb          
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-nb              
Hit [http://dl.google.com](http://dl.google.com) stable Release                                         
Get:7 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]         
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Translation-nb          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-nb            
Get:8 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]                       
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-nb                        
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-nb                 
Hit [http://dl.google.com](http://dl.google.com) stable/non-free Packages                               
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-nb           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-nb
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-nb
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-nb
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/main Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/restricted Packages                       
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/main Sources                              
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/restricted Sources                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                      
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages                                
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/main Packages                     
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/main Sources  
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages
Fetched 9B in 1s (8B/s)
Leser pakkelister ... Ferdig
johnny@johnny-laptop:~$ 
johnny@johnny-laptop:~$ 
johnny@johnny-laptop:~$ sudo aptitude install automatix2
Leser pakkelister ... Ferdig
Skaper oversikt over avhengighetsforhold       
Reading state information ... Ferdig    
Reading extended state information       
Initializing package states ... Ferdig
Building tag database ... Ferdig      
The following packages are BROKEN:
  skype 
The following packages have been automatically kept back:
  linux-image-2.6.17-10-generic linux-restricted-modules-2.6.17-10-generic 
  linux-restricted-modules-common 
The following packages have been kept back:
  avahi-daemon capplets-data evince gdm gimp gimp-data gimp-python 
  gnome-control-center gnome-games gnome-games-data gnome-system-tools 
  gnupg info language-pack-en language-pack-gnome-en libavahi-client3 
  libavahi-common-data libavahi-common3 libavahi-core4 libavahi-glib1 
  libgimp2.0 libgnome-window-settings1 libgnomeprintui2.2-0 
  libgnomeprintui2.2-common libgnomevfs2-0 libgnomevfs2-bin 
  libgnomevfs2-common libgnomevfs2-extra libgsf-1-114 libgsf-1-common 
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libmagick9 
  libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-data-tds1.0-cil 
  libmono-security1.0-cil libmono-sharpzip0.84-cil libmono-sqlite1.0-cil 
  libmono-system-data1.0-cil libmono-system-web1.0-cil 
  libmono-system1.0-cil libmono0 libmono1.0-cil libpng12-0 
  linux-headers-2.6.17-10 linux-headers-2.6.17-10-generic mono-common 
  mono-gac mono-jit mono-runtime openoffice.org openoffice.org-base 
  openoffice.org-calc openoffice.org-common openoffice.org-core 
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome 
  openoffice.org-gtk openoffice.org-impress openoffice.org-java-common 
  openoffice.org-math openoffice.org-style-default 
  openoffice.org-style-industrial openoffice.org-writer python-uno screen 
  sun-java5-bin tar ttf-opensymbol vino x11-common xbase-clients xorg 
  xserver-xorg xserver-xorg-input-all xserver-xorg-video-all xutils 
0 packages upgraded, 0 newly installed, 0 to remove and 83 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
[COLOR="Red"]The following packages have unmet dependencies:
  skype: Avhenger av: libqt3-mt but it is not installable or
                      libqt3c102-mt (>= 3:3.3.3.2) which is a virtual package.[/COLOR]
Resolving dependencies...
E: Klarte ikke å finne en fil for pakken sun-java5-bin. Det kan bety at du må ordne pakken selv (fordi arkitekturen mangler).
The following actions will resolve these dependencies:

Install the following packages:
libqt3-mt [3:3.3.6-3ubuntu3 (edgy, edgy)]

Score is -19

Accept this solution? [Y/n/q/?] y
The following packages have been automatically kept back:
  linux-image-2.6.17-10-generic linux-restricted-modules-2.6.17-10-generic 
  linux-restricted-modules-common 
The following NEW packages will be automatically installed:
  libqt3-mt 
The following packages have been kept back:
  avahi-daemon capplets-data evince gdm gimp gimp-data gimp-python 
  gnome-control-center gnome-games gnome-games-data gnome-system-tools 
  gnupg info language-pack-en language-pack-gnome-en libavahi-client3 
  libavahi-common-data libavahi-common3 libavahi-core4 libavahi-glib1 
  libgimp2.0 libgnome-window-settings1 libgnomeprintui2.2-0 
  libgnomeprintui2.2-common libgnomevfs2-0 libgnomevfs2-bin 
  libgnomevfs2-common libgnomevfs2-extra libgsf-1-114 libgsf-1-common 
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libmagick9 
  libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-data-tds1.0-cil 
  libmono-security1.0-cil libmono-sharpzip0.84-cil libmono-sqlite1.0-cil 
  libmono-system-data1.0-cil libmono-system-web1.0-cil 
  libmono-system1.0-cil libmono0 libmono1.0-cil libpng12-0 
  linux-headers-2.6.17-10 linux-headers-2.6.17-10-generic mono-common 
  mono-gac mono-jit mono-runtime openoffice.org openoffice.org-base 
  openoffice.org-calc openoffice.org-common openoffice.org-core 
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome 
  openoffice.org-gtk openoffice.org-impress openoffice.org-java-common 
  openoffice.org-math openoffice.org-style-default 
  openoffice.org-style-industrial openoffice.org-writer python-uno screen 
  sun-java5-bin tar ttf-opensymbol vino x11-common xbase-clients xorg 
  xserver-xorg xserver-xorg-input-all xserver-xorg-video-all xutils 
The following NEW packages will be installed:
  libqt3-mt 
0 packages upgraded, 1 newly installed, 0 to remove and 83 not upgraded.
Need to get 0B of archives. After unpacking 8921kB will be used.
Do you want to continue? [Y/n/?] y
[COLOR="Red"]Writing extended state information ... Feil
E: Klarte ikke å finne en fil for pakken sun-java5-bin. Det kan bety at du må ordne pakken selv (fordi arkitekturen mangler).
E: Couldn't lock list directory..are you root?
johnny@johnny-laptop:~$ [/COLOR]


I have marked in red lines that I think may indikate some problem.


Automatix2 Error and Information Report keeps giving error messages when trying to install new plug ins.

Flash plug-in gives this error message:

FATAL ERROR: Flash Player
An apt-based error occured and installation was unsuccessful.


Do any have a clue what is wrong?


Thank you!

---

### Post by Pinon on 2006-12-28
**[COLOR="Red"]AUTOMATIX2 RUNS NOW SMOOTHLY[/COLOR]**

Now the system really show off real potential, at last!

The thing I had to do was klikking System | Administration | Updating handler (translated from norwegian, it may be other names in english)

Then the system told what commands to write in the Terminal. Then after the system updated, things ran smoothly, including the Automatix2.

Kaze kleust. ( Oh mama, my poor engleski.)  :rolleyes:

---

