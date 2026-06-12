---
title: "Resolution issue"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by jgf621 on 2006-12-26
I am brand new to this and have received advice on how to fix my resolution problem.  None have worked.

I am limited to 800 x 600 and need 1280 x 1024.

Graphic adapter is   ATI RADEON XPRESS 200 Series
Monitor is               Samsung (SYNCMASTER) 931B Analog 19" monitor running at 70 hz.

Any advice that I can understand will be most appreciated.

Thanks,

Joe](*,)

---

### Post by taurus on 2006-12-26
Did you install an ATI driver for your graphic card?

[http://albertomilone.com/driver_edgy.html](http://albertomilone.com/driver_edgy.html)

---

### Post by jgf621 on 2006-12-26
I tried.  I printed out Alberto's instructions but the gpg -- Export line reported "Nothing to export".  After that, nothing else worked.

---

### Post by taurus on 2006-12-26
Tell me exactly what you did or ran?

```

wget http://www.albertomilone.com/drivers/tseliot.asc
gpg --import tseliot.asc
gpg --export --armor albertomilone@alice.it | sudo apt-key add -

```

---

### Post by jgf621 on 2006-12-26
Here's what I ran with responses

wget [http://www.albertomilone.com/drivers/tseliot.asc](http://www.albertomilone.com/drivers/tseliot.asc)

--13:12:04--  [http://www.albertomilone.com/drivers/tseliot.asc](http://www.albertomilone.com/drivers/tseliot.asc)
           => `tseliot.asc'
Resolving [www.albertomilone.com](www.albertomilone.com)... 68.178.232.90
Connecting to www.albertomilone.com|68.178.232.90|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,704 (1.7K) [text/plain]

100%[====================================>] 1,704         --.--K/s             

13:12:04 (65.00 MB/s) - `tseliot.asc' saved [1704/1704]

gpg --import tseliot.asc

gpg: directory `/home/jgf/.gnupg' created
gpg: new configuration file `/home/jgf/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/jgf/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/jgf/.gnupg/secring.gpg' created
gpg: keyring `/home/jgf/.gnupg/pubring.gpg' created
gpg: /home/jgf/.gnupg/trustdb.gpg: trustdb created
gpg: key 8EB26AF1: public key "Alberto Milone (tseliot) <albertomilone@alice.it>" imported
gpg: Total number processed: 1
gpg:               imported: 1

gpg --export --armor [email]albertomilone@alice.it[/email] | sudo apt-key add -


Password:
OK

These responses are different from last time I ran them.  Now where do I run next command

deb http:/www.albertomilone.com/drivers/edgy/nonlegacy/64bit binary/

It says Bash when I run it in terminal.

Thanks,

Joe

---

### Post by taurus on 2006-12-26
You need to add that line, **deb http:/www.albertomilone.com/drivers/edgy/nonlegacy/64bit binary/**, to the end of your /etc/apt/sources.list!!!

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by jgf621 on 2006-12-26
Bear with me.  I suspect the tree !'s are your way of showing frustration.

I got by that and have added     to the file.

When I run the sudo aptitude update I get the following message

Err [http://www.albertomilone.com](http://www.albertomilone.com) binary/ Packages                               
  404 Not Found


I have entered all of these commands in this order.

wget [http://albertomilone.com/drivers/tseliot.asc](http://albertomilone.com/drivers/tseliot.asc)

gpg --import tseliot.asc

gpg --export --armor [email]albertomilone@alice.it[/email] | sudo apt-key add -

sudo nano -w /etc/apt/sources.list

sudo aptitude update

Thanks for your help

---

### Post by taurus on 2006-12-26
What does your /etc/apt/sources.list look like then?

```
cat /etc/apt/sources.list
```

---

### Post by jgf621 on 2006-12-27
Here's what I get -

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb [http://www.albertomilone.com/drivers/edgy/nonlegacy/64bit](http://www.albertomilone.com/drivers/edgy/nonlegacy/64bit) binary/

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by jgf621 on 2006-12-27
I noticed the last one I pasted showed an error.  This is the actual sources.list that I copied.


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb [http://www.albertomilone.com/drivers/edgy/nonlegacy/64bit](http://www.albertomilone.com/drivers/edgy/nonlegacy/64bit) binary/

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by jgf621 on 2006-12-27
Is there a reason when I post that it changes characters in the line
[http://www.albertomilone.com/drivers/nonlegacy/64bit](http://www.albertomilone.com/drivers/nonlegacy/64bit) binary/ to
[http://www.albertomilone.com/drivers...onlegacy/64bit](http://www.albertomilone.com/drivers...onlegacy/64bit) binary/   ?

Thanks

Joe

---

### Post by Henry Rayker on 2006-12-27
deb [http://www.albertomilone.com/drivers...onlegacy/64bit](http://www.albertomilone.com/drivers...onlegacy/64bit) binary/
should that line be 
deb http:/www.albertomilone.com/drivers/edgy/nonlegacy/64bit binary
perhaps the / was throwing it off at the end...

---

### Post by taurus on 2006-12-27
And you get an error message about the "deb [http://www.albertomilone.com/drivers...onlegacy/64bit](http://www.albertomilone.com/drivers...onlegacy/64bit) binary/" when you run "sudo aptitude update"?

---

### Post by taurus on 2006-12-27
> **jgf621 said:**
> Is there a reason when I post that it changes characters in the line
[http://www.albertomilone.com/drivers/nonlegacy/64bit](http://www.albertomilone.com/drivers/nonlegacy/64bit) binary/ to
[http://www.albertomilone.com/drivers...onlegacy/64bit](http://www.albertomilone.com/drivers...onlegacy/64bit) binary/   ?

Thanks

Joe
Try to use the "```
" thing...

[code]

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb http://www.albertomilone.com/drivers/nonlegacy/64bit binary/

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```

---

### Post by jgf621 on 2006-12-27
No, I get it when I do the sudo aptitude update.  Here's the whole response to that.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US         
Ign [http://www.albertomilone.com](http://www.albertomilone.com) binary/ Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://www.albertomilone.com](http://www.albertomilone.com) binary/ Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://www.albertomilone.com](http://www.albertomilone.com) binary/ Release                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Ign [http://www.albertomilone.com](http://www.albertomilone.com) binary/ Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources      
Err [http://www.albertomilone.com](http://www.albertomilone.com) binary/ Packages                    
  404 Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Fetched 3B in 0s (3B/s)
Reading package lists... Done

---

### Post by jgf621 on 2006-12-28
I solved this issue.  There was an error.   

deb [http://www.albertomilone.com/drivers/edgy/nonlegacy/64bit](http://www.albertomilone.com/drivers/edgy/nonlegacy/64bit) binary/  needs to be
deb  [http://www.albertomilone.com/drivers/edgy/latest/64bit](http://www.albertomilone.com/drivers/edgy/latest/64bit) binary/

I saw this was changed on Alberto Milone's web site when I went poking around..  Once I changed it in the source.list, and followed the other instructions, all is well.  I learned a little and am now ready to some serious damage.

Thank you for your help.:mrgreen:

---

### Post by in_flu_ence on 2006-12-28
I have the same graphic chip as yours. What I found is the change the /etc/X11/xorg.conf.

I have changed as follows:

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200 (RS482)"
	Driver		"ATI"
	BusID		"PCI:1:5:0"

to

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200 (RS482)"
	Driver		"vesa"
	BusID		"PCI:1:5:0"

It allows me to go to my highest resolution of my screen.

Maybe not the best tweak but possibly the best and least risky tweak.

Hope it helps.

---

### Post by jgf621 on 2006-12-29
Thank you.  I wish I'd seen that before I incurred so many brain aches.  I need to get more familiar with the language and environment.  Just typing the commands with no understanding is a struggle leading to typos, etc.

Good news is now I that have proper resolution I can attack other issues.

happy New Year!:???:

---

### Post by in_flu_ence on 2006-12-30
So what's your solution to your problem? jgf621?

WIll be good to know 'cause I want to make sure I did the right thing myself as well:P

---

### Post by jgf621 on 2006-12-30
I followed the instructions at [http://albertomilone.com/driver_edgy.html](http://albertomilone.com/driver_edgy.html)   except changing 

deb [http://www.albertomilone.com/drivers...onlegacy/64bit](http://www.albertomilone.com/drivers...onlegacy/64bit) binary/ to
deb [http://www.albertomilone.com/drivers/edgy/latest/64bit](http://www.albertomilone.com/drivers/edgy/latest/64bit) binary/

The instructions for adding the driver worked fine but the author changed the location as indicated.

---

