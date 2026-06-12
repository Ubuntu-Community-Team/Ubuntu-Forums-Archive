---
title: "Official Xubuntu User!!!!!!!"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by Fireware on 2007-01-07
I finally installed my first linux operating system, Xubuntu using the alternate CD. It is installing now!!!!

---

### Post by Praxicoide on 2007-01-07
Congrats!

---

### Post by MkfIbK7a on 2007-01-07
good luck hope you like xubuntu!:D

---

### Post by Praxicoide on 2007-01-07
So what made you choose Xubuntu over Dreamlinux?

---

### Post by psycosmyth on 2007-01-07
Welcome to reality!
Enjoy it, come here often, and use the search feature for most of your questions.
We are a friendly bunch so dive in!:mrgreen:

---

### Post by Fireware on 2007-01-07
> **Praxicoide said:**
> So what made you choose Xubuntu over Dreamlinux?

Better support, better for my low memory desktop. :)

Does it take awhile to install?

---

### Post by Fireware on 2007-01-07
It said, "Installation Step Failed: The failing step: Select and Install Software. 

What do I do? will it not install now?

---

### Post by Frak on 2007-01-07
Did you check your md5 checksum before you installed?

---

### Post by Fireware on 2007-01-07
I didn't burn the cd.

---

### Post by Fireware on 2007-01-07
It installed, but said Unable to locate RSD something..... but it installed.


the alternate cd does not have a GUI after it is installed?

---

### Post by MkfIbK7a on 2007-01-07
just remove the cd and boot the computer see what happens

---

### Post by Fireware on 2007-01-07
I did, it ejected its self an restarted. I typed those sudo commands to install the xfce desktop...is that what I am suppose to do? 

I typed: sudo aptitude updates
sudo aptitude install xubuntu-desktop 

and it now says 50% [working] ...is that good?

---

### Post by Pobega on 2007-01-07
Means it's downloading the packages, so yes that's good.

---

### Post by Fireware on 2007-01-07
lol Oh. :)

---

### Post by Fireware on 2007-01-07
I think I messed up...I selected 'No Configuration' .... what does that mean?

---

### Post by MkfIbK7a on 2007-01-07
when did you select "no configuration" as you say

---

### Post by PriceChild on 2007-01-07
> **Fireware said:**
> I think I messed up...I selected 'No Configuration' .... what does that mean?I'm guessing postfix

You've done well :)

Nothing's broken, you should be fine!

---

### Post by Fireware on 2007-01-07
> **PriceChild said:**
> I'm guessing postfix

You've done well :)

Nothing's broken, you should be fine!

Yeah..there. 

Yay! lol :)

So after all this my Xubuntu will have a GUI?

---

### Post by Fireware on 2007-01-07
The screen went black.....what do i do now?

EDIT: lol nevermind, computer just went to sleep or w/e.

---

### Post by Fireware on 2007-01-07
Is it suppose to take awhile installing the xfce desktop?

---

### Post by MkfIbK7a on 2007-01-07
yes it should take about 30 min on dsl not sure about dialup...

---

### Post by Fireware on 2007-01-07
Ok.....

I want to thank you all for helpig me with Xubuntu. I'll be sure to come here if I have any more questions or problems. Thanks again. :)

---

### Post by Delkster on 2007-01-07
> **Fireware said:**
> Is it suppose to take awhile installing the xfce desktop?

Probably yes. Depends on which stage of the installation you mean, though. Downloading stuff probably takes a bit of time depending on you connection (quite obviously), and after that unpacking, installing and auto-configuring the downloaded packages probably takes a while as well. At that point it shouldn't get stuck without any output for a very long time, though. It usually keeps on showing what it's working on and that should change every once in a while.

The GUI in Xubuntu may not really be soaked in features so perhaps you should expect to get in touch with the command line even after getting the GUI running, though. Don't be afraid, it's not an enemy (in fact for me it's a good friend), but the more lightweight desktop does also mean less features and thus a more likely return to the text terminal.

---

### Post by Frak on 2007-01-07
And yes it has a GUI, the XFCE desktop enviroment.

---

### Post by Fireware on 2007-01-07
This came up: 

Errors were encountered while processing: xubuntu-desktop . 

what do i do?

---

### Post by Fireware on 2007-01-07
It says Unable to locate RSDP.........

But if I let it sit in the screen it then changes and begins loading the xfce desktop......

whats going on...did it install, cuz its coming up...but i had gotten that error message above.

---

### Post by MkfIbK7a on 2007-01-07
if its coming up i say leave it alone until it has a problem then try to fix it:mrgreen:

---

### Post by riven0 on 2007-01-07
Most likely there was a certain package that didn't install correctly. When xfce comes up, open the terminal and try doing **sudo dpkg --configure -a** and then **sudo apt-get install xubuntu-desktop** and see if that'll fix whatever package is missing.

---

### Post by Fireware on 2007-01-08
Okay I will. I have a few more questions. 

1. Why does my mouse move so slow? It moves not when I move the mouse...like a delay or something. 

2. How do I adjust the screen? The right hand side of the desktop is off the screen on the right side.

---

### Post by Fireware on 2007-01-08
> **riven0 said:**
> Most likely there was a certain package that didn't install correctly. When xfce comes up, open the terminal and try doing **sudo dpkg --configure -a** and then **sudo apt-get install xubuntu-desktop** and see if that'll fix whatever package is missing.


I did that and it said: 

xubuntu-desktop: Depends: xubuntu-system tools but is not going to be installed or gnome-system tools but is not installable. 
E: Unmet dependencies. Try 'apt-get -f install' with no package (or specify a solution) 


it also said reading package lists....done
building dependecy tree
reading state information....done
xubuntu-desktop is already the newest version

---

### Post by Frak on 2007-01-08
What are the specs of your system.

---

### Post by Fireware on 2007-01-08
I think I typed it wrong....I'm going to try again tom.

---

### Post by livinginx on 2007-01-08
I installed Xubuntu onto an eMachines eOne 400 the other day.  Currently running Ubuntu Edgy on both of my main PCs.

If you post your specs, we could probably help you better.

---

