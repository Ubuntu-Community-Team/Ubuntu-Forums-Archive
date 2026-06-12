---
title: "feisty up and running.. probs with epiphany and opera!"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by beanco on 2007-09-10
so after taking care of my x server issues I just upgraded to feisty from dapper

I have a few issues that are bugging me and I cannot figure them out...


opera won't launch.. i get this when i try from the command line
Quote:

[PHP]
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
Segmentation fault[/PHP]


epiphany will not launch. I get this

[PHP]
(epiphany:5863): libgnomevfs-WARNING **: Failed to create service browser: Bad state


Quote:
(epiphany:5863): libgnomevfs-WARNING **: Failed to create service browser: Bad state


(epiphany:5863): libgnomevfs-WARNING **: Failed to create service browser: Bad state


** ERROR **: file ephy-node.c: line 1061 (ephy_node_new_from_xml): should not be reached
aborting...
Aborted[/PHP]

and whatever that panel/bar is at the bottom showing what is open.. I cannot see it.. I have to keep usingalt+tab to switch between open prgms. I find this annoying.

The monitor is vibrating and bugging my eyes.... I tried to set the resolution but it is not helping.

robi

---

### Post by asmoore82 on 2007-09-10
had you used Automatix on Dapper?

---

### Post by beanco on 2007-09-10
well before I had the Xserver issues it had actually dissappeared form the applicaitons menu... i was going to dig round to see why but the Xserver was more serious...

now i just want to get opera running... need to get stuff out of there ... 


Just noticed I cannot see the clock!!!!! date!!! where are they?

robi

---

### Post by asmoore82 on 2007-09-10
> **beanco said:**
> well before I had the Xserver issues [SIZE="6"]it[/SIZE] had actually dissappeared form the applicaitons menu

I assume that "it" is Automatix and that you did have/use it at one point on your Install.

I am sorry but you are pretty much screwed...
attempting to clean up the mess left behind by poorly written code (Automatix)
is more trouble than it is worth; I suggest a complete re-install.

Spread the Word that Automatix BREAKS systems!

for a more comprehensive list of WHY Automatix SUCKS,
see: [http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)

---

### Post by beanco on 2007-09-10
yeha, IT was Automatix... but IT is not even in the applicaitons menue on this new install/upgrade.

if you sy it sucks, that is fine with me... what to use? command line? great, powerful stuff but confusing for n00bs like me.


I still want to get opera and epiphany running!!! any ideas?

robi

---

### Post by asmoore82 on 2007-09-10
> **beanco said:**
> yeha, IT was Automatix... but IT is not even in the applicaitons menue on this new install/upgrade.

if you sy it sucks, that is fine with me... what to use? command line? great, powerful stuff but confusing for n00bs like me.


I still want to get opera and epiphany running!!! any ideas?

robi

:confused: Automatix is most definitely not a part of a fresh install ...
so, did you install/use it at any point prior to the upgrade or not?

---

### Post by Terl on 2007-09-10
> **beanco said:**
> yeha, IT was Automatix... but IT is not even in the applicaitons menue on this new install/upgrade.

if you sy it sucks, that is fine with me... what to use? command line? great, powerful stuff but confusing for n00bs like me.


I still want to get opera and epiphany running!!! any ideas?

robi

For the video drivers:  I use restricted driver manager

For other programs:  I use synaptic or just terminal and apt-get

You do not need automatix.  Read the link posted above about the shortcomings of automatix.

---

### Post by beanco on 2007-09-10
i used autoamtix on the old install and did not actually like it.


i have not used it on the new install/upgrade. and I do not plan on using it..

there are a few things I want to learn and the p0ower o fthe command line is one of them... apt -get  and such things... but like i keep saying, it is all so confusing to me.


robi

---

### Post by asmoore82 on 2007-09-10
> **beanco said:**
> i used autoamtix on the old install and did not actually like it.

i have not used it on the new install/upgrade. and I do not plan on using it..

there are a few things I want to learn and the p0ower o fthe command line is one of them... apt -get  and such things... but like i keep saying, it is all so confusing to me.

robi

you keep using the expression "new install/upgrade" ... this does not make any sense.
the current state of your system can only be one or the other ...
A new install -OR- an upgrade [of an old install].

automatix is very poorly written software that makes a successful upgrade almost impossible;
even if you just "tried it out;" the only way to make sure all traces of automatix's mischief are
gone from your system is to do a real "new install," upgrading is not enough.

---

### Post by hyper_ch on 2007-09-10
If you have troubles installing something that automatix offers you can ask here for help ;)

---

### Post by beanco on 2007-09-10
OK, so I will clarify.

I had dapper yesterday, now I have Feisty, that is an upgrade then!


I had a coworker who is linux saavy help.. actually he did it all while I was teaching.... and I did not say anything to him aobut automatix and I do not see it in teh applications menu.

but if you tell me how to check for certain that it is not here and if it is here how to delete itI will promptly do so.

robi

---

### Post by asmoore82 on 2007-09-10
> **beanco said:**
> I had dapper yesterday, now I have Feisty, that is an upgrade then!


how _long_ ago did you install Dapper?

_unless_ Dapper was a fresh install yesterday morning,
was automatix ever used on that Dapper?

---

### Post by beanco on 2007-09-10
Dapper was installed around last Christmas.

I did use Automatix on it.

I have not used it on Feisty


robi

---

### Post by diatribe on 2007-09-10
you will more than likely need to reinstall

---

### Post by beanco on 2007-09-10
Ubuntu or just Opera?

---

### Post by toasterofirony on 2007-09-10
The Whole Shebang.

And next time, if you want Opera, download the .deb from the Opera site.

If you want your nvidia driver, try using "envy"

---

### Post by beanco on 2007-09-10
too bad.... gergo, my colleague spent a lot time... well he had other things to do so it seemed like a lot of time... installing feisty.... 

so spare  me the hssle of figuring it out... tell me how to reinstall with one nice coommand line thingy and i will try it....

then I will figure out how to do the opera bit.

thanks


robi

ps. will reinstalling give me

epiphany

sympatic or whatever that package thingy is called?

---

### Post by toasterofirony on 2007-09-10
Ugh.

Installing Ubuntu is very, very, very easy. You don't need help. Just a disc and a few minutes of your time. Just make sure you back everything up first, to avoid tears and tantrums.

And yes, you get the Synaptic "thingy" when you re-install. From there you can install epiphany (though why you would choose it over Firefox, I don't know) and if you want Opera you can download the package from the Opera website. Tres simple, no?

---

### Post by beanco on 2007-09-10
I thought it was so simple but with all the xserver probs I had over the weekend I have lost my nerve.


Epiphany instead of FF? Well, I just wanted to try it out. I used it once a few months ago and actually liked it.

What I really like about Opera is the that 1. it saves sessions... If I have several tabs open and there is a crash, a power outage, I have to leave, whatever, when I start her back up all the tabs are there... I cannot do this in FF, not sure about Epiphany, bt it is one thing I will look for. I also like the email client!!!

So, what is the easiest, fastest, safest way to reinstall?


what is the easiest way to copy/back up everything onto a DVD? There has to be some copy /everything command I cna use in terminal....

And while I am at it asking for tons of advice..... what is the best place to look to learn the very basics of linux/ubuntu.... maybe the ubuntu home page has good tutorials now... I will look.

robi

---

### Post by toasterofirony on 2007-09-10
1) For backing stuff up, if you've got a spare external hard-drive, then use that. If you don't, but you can use blank DVD's. Personally, I just drag and drop. If you really, really must use the command line, then "cp" is the command you want:

cp /home/all the files you want to copy /media/whatever you're copying onto

2) Download an .iso for Ubuntu from the Ubuntu site. Burn it to a blank CD. Reboot.

3) Follow instructions.

4) Once installed, check out the firefox extensions for saving sessions, that is the functionality you like so much in Opera.

5) [https://help.ubuntu.com/](https://help.ubuntu.com/) this site will do exactly what it says on the tin.

---

### Post by philinux on 2007-09-10
> What I really like about Opera is the that 1. it saves sessions... If I have several tabs open and there is a crash, a power outage, I have to leave, whatever, when I start her back up all the tabs are there... I cannot do this in FF

Firefox saves session automatically if there is a crash or you shutdown

---

### Post by beanco on 2007-09-10
> **toasterofirony said:**
>  ...
1) 
cp /home/all the files you want to copy /media/whatever you're copying onto

so we have 5 persons on this computer, ie. /home/robi and /home/ancsi etc. if I type in 

cp /home/ media/cd   

will I get everything under the home menus copied onto a cd or dvd if I type DVD? Is it that easy?

Or just go to places/computer/ and start dragging /home to.... to where???




[HTML]2) Download an .iso for Ubuntu from the Ubuntu site. Burn it to a blank CD. Reboot.[/HTML]

I actually did this the other day... I have a CD with an Ubuntu .iso on it.... but I cannot get anything to open on it... I will just make a new one then...


[HTML]3) Follow instructions.[/HTML]

I assume these will *pop* open/up if the CD has been burned correctly....


[HTML]4) Once installed, check out the firefox extensions for saving sessions, that is the functionality you like so much in Opera.
[/HTML]

Thanks for the info.... I have no idea what extensions are, I have read the word before...but not really grasped the concept....

```
5) [https://help.ubuntu.com/](https://help.ubuntu.com/) this site will do exactly what it says on the tin.
```

off to read it momentarily.

Thanks for the help!

robi

---

### Post by beanco on 2007-09-10
> **philinux said:**
> Firefox saves session automatically if there is a crash or you shutdown


I thought that is what it should do...

I had two tabs open, closed FF and then relaunched it... but it did not save the sessions!

robi

---

### Post by asmoore82 on 2007-09-10
> **beanco said:**
> I thought that is what it should do...

I had two tabs open, closed FF and then relaunched it... but it did not save the sessions!

robi

in Firefox, open "Edit -> Preferences"
Under "Main," the first tab,
in "Startup," the first section,
and set "When ff starts," the very first option,
to "Show * from last time"

---

### Post by toasterofirony on 2007-09-10
So...

1)If the contents of your home folder(s) is less than 4.7 gig burn it onto a DVD via a program of your choosing (K3b, Brasero, whatever). If not, divide these files up in a way that lets you burn them onto *several* DVD's.

2)Then use your CD/ DVD burning program of choice to burn the Ubuntu .iso file onto a blank CD. Make sure you burn it as an "image" rather than a "data" disc. Otherwise it will not work.

3)Once you have this disc, leave it in the machine and reboot. Hopefully your computer is setup so that it will boot from CD. If not, get your mate to sort this out for you. I cannot explain it here, adequately.

4)If and when the CD boots, follow the guide to install Ubuntu.

5) Report back that everything works so I can weep with relief.

---

