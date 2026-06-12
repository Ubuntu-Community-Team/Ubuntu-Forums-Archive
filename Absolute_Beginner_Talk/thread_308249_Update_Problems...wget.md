---
title: "Update Problems...wget"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by ebozzz on 2006-11-27
I just received new updates on yesterday and it will not let me install them. I get the following error messages:

[COLOR="Blue"]E: Type 'wget' is not known on line 34 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.[/COLOR]

then....

[COLOR="Blue"]Could not upgrade the system!
Fix broken packages first.[/COLOR]

Can someone clue me in on what I need to do to correct this? Also, which books on Ubuntu are the best? I'm going shopping. Thanks!

---

### Post by kelbizzle on 2006-11-27
I may be wrong but you can check. Type:

```
 sudo gedit /etc/apt/sources.list
```

Check out line 34 and see if it looks like wget doesn't belong there take it out. I just checked mine out, I dont have wget anywhere in mine. Maybe you copy and pasted something in there? I'm just guessing.

---

### Post by taurus on 2006-11-27
> **kelbizzle said:**
> I may be wrong but you can check. Type:

```
 sudo gedit /etc/apt/sources.list
```

Check out line 34 and see if it looks like wget doesn't belong there take it out. I just checked mine out, I dont have wget anywhere in mine. Maybe you copy and pasted something in there? I'm just guessing.
I bet he just copied and pasted the wrong line from automatix's site in there, the one that you supposed to run it from a terminal!!!  ;)

---

### Post by ebozzz on 2006-11-27
> **kelbizzle said:**
> I may be wrong but you can check. Type:

```
 sudo gedit /etc/apt/sources.list
```

Check out line 34 and see if it looks like wget doesn't belong there take it out. I just checked mine out, I dont have wget anywhere in mine. Maybe you copy and pasted something in there? I'm just guessing.

I do not remember copying and pasting anything in there. I simply clicked on the indicator on the task bar. Here's what I have from your command:


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

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
[COLOR="Blue"]wget [http://www.getautomatiz.com/apt/key.gpg.asc](http://www.getautomatiz.com/apt/key.gpg.asc)
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C
sudo apt-key add -
sudo apt-get update
sudo apt-get install automatix2[/COLOR]

exit
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe

Is the highlighted portion the problem?

---

### Post by ebozzz on 2006-11-27
> **taurus said:**
> I bet he just copied and pasted the wrong line from automatix's site in there, the one that you supposed to run it from a terminal!!!  ;)

Hey Taurus. You may be right. take a look at what I have and tell me what to do, please?:oops:

---

### Post by taurus on 2006-11-27
I knew it!!!  

You need to remove these lines from your /etc/apt/sources.list because you're supposed to type them from a terminal, not adding them to your /etc/apt/sources.list...

```

wget http://www.getautomatiz.com/apt/key.gpg.asc
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C
sudo apt-key add -
sudo apt-get update
sudo apt-get install automatix2

```
Then, add this line to the end of your /etc/apt/sources.list.

```

deb http://www.getautomatix.com/apt edgy main

```
Now, run (from a terminal)

```

wget http://www.getautomatix.com/apt/key.gpg.asc
 gpg --import key.gpg.asc
 gpg --export --armor 521A9C7C | sudo apt-key add -
sudo apt-get update
sudo apt-get install automatix2

```

---

### Post by ebozzz on 2006-11-27
Alright, I wnet in and removed this portion......

[COLOR="Blue"]wget [http://www.getautomatiz.com/apt/key.gpg.asc](http://www.getautomatiz.com/apt/key.gpg.asc)
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C
sudo apt-key add -
sudo apt-get update
sudo apt-get install automatix2

exit[/COLOR]

After saving it it appears that all is well. Thanks for the help. Now which of the Ubuntu books would considered required reading for a newbie such as myself?

---

### Post by taurus on 2006-11-27
Make sure you add the line that I included from above to your /etc/apt/sources.list so apt-get can find automatix2 for you.  Just did a quick search on amazon.com and found a few...

[http://www.amazon.com/s/ref=nb_ss_gw/103-1305326-4970229?url=search-alias%3Dstripbooks&field-keywords=ubuntu+books&Go.x=10&Go.y=9&Go=Go](http://www.amazon.com/s/ref=nb_ss_gw/103-1305326-4970229?url=search-alias%3Dstripbooks&field-keywords=ubuntu+books&Go.x=10&Go.y=9&Go=Go)

---

### Post by ebozzz on 2006-11-27
> **taurus said:**
> Make sure you add the line that I included from above to your /etc/apt/sources.list so apt-get can find automatix2 for you.  Just did a quick search on amazon.com and found a few...

[http://www.amazon.com/s/ref=nb_ss_gw/103-1305326-4970229?url=search-alias%3Dstripbooks&field-keywords=ubuntu+books&Go.x=10&Go.y=9&Go=Go](http://www.amazon.com/s/ref=nb_ss_gw/103-1305326-4970229?url=search-alias%3Dstripbooks&field-keywords=ubuntu+books&Go.x=10&Go.y=9&Go=Go)

Done. Thank you! Thank you! =D> 

I was looking at those books on Amazon. I was leaning towards *The Official Ubuntu Book* and *Beginning Ubuntu Linux: From Novice to Professional*. Do you have any personal experience with either of them?

---

### Post by taurus on 2006-11-27
> **ebozzz said:**
> Done. Thank you! Thank you! =D> 

Got your automatix2 now!

> I was looking at those books on Amazon. I was leaning towards *The Official Ubuntu Book* and *Beginning Ubuntu Linux: From Novice to Professional*. Do you have any personal experience with either of them?

Not really.  Since I have not seen them or browsed them, I can't comment on them because that wouldn't be fair.  But from the quick overview, they seem to be good!  ;)   I guess you can go to your local bookstores to see if they carry those two titles.  Do some quick reading through them to get a feel and see if you like the style written in the books.  That's probably the best way to judge whether you like the books or not...

---

### Post by kelbizzle on 2006-11-27
> **taurus said:**
> I knew it!!! 

lol

---

### Post by ebozzz on 2006-11-27
> **kelbizzle said:**
> lol

LOL is right!:D ;)

---

### Post by taurus on 2006-11-27
> **ebozzz said:**
> LOL is right!:D ;)
:-$  is even better!

---

### Post by ebozzz on 2006-11-27
> **taurus said:**
> Got your automatix2 now!



Not really.  Since I have not seen them or browsed them, I can't comment on them because that wouldn't be fair.  But from the quick overview, they seem to be good!  ;)   I guess you can go to your local bookstores to see if they carry those two titles.  Do some quick reading through them to get a feel and see if you like the style written in the books.  That's probably the best way to judge whether you like the books or not...

Neither of them are in my local stores. I have seen *Ubuntu Unleashed* and *Moving to Ubuntu*. Can't afford to buy them all so I'm hoping to hit with the initial purchases.

---

### Post by taurus on 2006-11-27
I guess either one of those two titles from amazon.com is good.  The used copies are just as expensive as the new ones...  I guess the first three titles from the link that I sent are new, August 2006, so probably get The Office Ubuntu Book then!

Remember, it is covered the Dapper version, 6.06LTS but it would apply to Edgy and later releases as well.  Just want you to aware of that.

---

### Post by ebozzz on 2006-11-27
Understood. I'm going to make my move. Thanks for the help, _*again*_.

---

### Post by fusionisthefuture on 2007-03-03
ive got the a similar, but slightly different problem.  i just upgraded to edgy from dapper and now im trying to install my nvidia drivers with beryl, following this guide: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia#Automatic_installation](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia#Automatic_installation)
and i added the repository like he said to, and then when i run 
sudo apt-get update && sudo apt-get install linux-restricted-modules-$(uname -r) nvidia-glx 
i get:
E: Type 'repository' is not known on line 34 in source list /etc/apt/sources.list
i have never copied or pasted anything into my /apt/sources.list file, and heres what it looks like currently.  

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
# deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) dapper free non-free
# deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) dapper free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

# deb [http://www.albertomilone.com/drivers/dapper/latest/64bit](http://www.albertomilone.com/drivers/dapper/latest/64bit) binary/
# deb [http://www.albertomilone.com/drivers/dapper/newlegacy/64bit](http://www.albertomilone.com/drivers/dapper/newlegacy/64bit) binary/
# deb [http://www.albertomilone.com/drivers/dapper/legacy/64bit](http://www.albertomilone.com/drivers/dapper/legacy/64bit) binary/
deb [http://nvidia.limitless.lupine.me.uk/ubuntu](http://nvidia.limitless.lupine.me.uk/ubuntu) edgy stable
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main

## nVidia driver repository
repository

## nVidia driver repository
repository

## nVidia driver repository
deb [http://nvidia.limitless.lupine.me.uk/ubuntu](http://nvidia.limitless.lupine.me.uk/ubuntu) edgy stable

## nVidia driver repository
deb [http://nvidia.limitless.lupine.me.uk/ubuntu](http://nvidia.limitless.lupine.me.uk/ubuntu) edgy stable

any ideas?
thanks
-arne

---

### Post by taurus on 2007-03-03
You need to remove these lines from your /etc/apt/sources.list.

```

## nVidia driver repository
repository

## nVidia driver repository
repository

## nVidia driver repository
deb http://nvidia.limitless.lupine.me.uk/ubuntu edgy stable

```

```
gksudo gedit /etc/apt/sources.list
```

---

