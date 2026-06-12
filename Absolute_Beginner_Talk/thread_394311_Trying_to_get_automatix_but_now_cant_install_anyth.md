---
title: "Trying to get automatix but now cant install anything"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by coollikestevie on 2007-03-26
I was following a guide here: [http://www.howtoforge.com/the_perfect_desktop_ubuntu6.10](http://www.howtoforge.com/the_perfect_desktop_ubuntu6.10)

and when these are the commands it told me to enter to install automatix.


> echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main" | sudo tee -a /etc/apt/sources.list


> 
wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -

These ones worked


> sudo apt-get update
> 
sudo apt-get install automatix2

However, these ones returend:
> 
stevieb@utnubu:~$ sudo apt-get update
E: Type 'wget' is not known on line 31 in source list /etc/apt/sources.list
stevieb@utnubu:~$ sudo apt-get install automatix2
E: Type 'wget' is not known on line 31 in source list /etc/apt/sources.list



And now when i try to open Add/Remove Programs it shows up with this error


> Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.

Also when i go to System>Administration>Synaptic Package Manager

> E: Type 'wget' is not known on line 31 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

---

### Post by oilchangeguy on 2007-03-26
what's with all the un-needed command line crap? simply go to [www.getautomatix.com](www.getautomatix.com) and click on the install tab, click on the easy install for your version and let the website do it's thing. also no need to use a command line for updates, you will be notified when they are available. look for a starburst icon to the left of the clock. and yes in linux there is more of a need to use the command line than in windows. but NOT for every friggen thing!

---

### Post by coollikestevie on 2007-03-26
calm down dude. i was just following what the guide told me... the problem is now i cant install anything at all.

---

### Post by oilchangeguy on 2007-03-26
don't know what to tell you on how to undo whatever it is that you've done. just be very wary of command line junkies. most things can be done without the use of the command line. and the use of the command line and the failure from doing something wrong with the command line is what gives most versions of linux their bad rep, as being hard to work with.

---

### Post by jackrobinson on 2007-03-26
> **coollikestevie said:**
> I was following a guide here: [http://www.howtoforge.com/the_perfect_desktop_ubuntu6.10](http://www.howtoforge.com/the_perfect_desktop_ubuntu6.10)

and when these are the commands it told me to enter to install automatix.
post the following:







These ones worked





However, these ones returend:



And now when i try to open Add/Remove Programs it shows up with this error




Also when i go to System>Administration>Synaptic Package Manager
```
cat /etc/apt/sources.list
```

---

### Post by coollikestevie on 2007-03-26
yes i am so smart! i fixed it :P i typed the first command in wrong and it put all this **** into the sources.list file.. i just had to go and edit it.

thanks for flaming me for following a command line junkie... but u know he got those commands straight of the automatix website.

---

### Post by oilchangeguy on 2007-03-26
glad you fixed it. my point is this, using the command line is much like using regedit in windows, if you're not careful you can, and will screw something up. and something as simple as installing automatix should be done with their website. not by using a command line.

---

### Post by coollikestevie on 2007-03-26
oh god regedit is horrible... i try to stay away from it

---

### Post by jackrobinson on 2007-03-26
> **coollikestevie said:**
> yes i am so smart! i fixed it :P i typed the first command in wrong and it put all this **** into the sources.list file.. i just had to go and edit it.

thanks for flaming me for following a command line junkie... but u know he got those commands straight of the automatix website.
the keyid is obsolete in that command list. Automatix has recently changed its GPG key. This howto you are using hasnt updated it yet.

---

### Post by arron on 2007-03-26
> **oilchangeguy said:**
> glad you fixed it. my point is this, using the command line is much like using regedit in windows, if you're not careful you can, and will screw something up. and something as simple as installing automatix should be done with their website. not by using a command line.

Ummmm not really....  The command prompt should not be something to be feared, you can screw the system with a gui just as easily as at the prompt.  By using the prompt you learn a lot more about Linux, and it opens up a lot more options.  Many applications are prompt only, and most advanced items are prompt only.  Then add scripts to it all and you can automate so much more.

My point is, I don't think you should trash those who know the shell or bash prompt, and no one should fear it.  If you want to learn more about how things work, which is a large amount of current Linux users, the prompt is great to know.  After reading a couple how to's and 10minutes of playing with a shell, it gets quite easy.

Prompt is safe, easy, and holds the power of Linux.

---

### Post by oilchangeguy on 2007-03-26
maybe my installs of ubuntu are the exception, and not the rule. no problems, (except internal modem, and i don't use dial-up, so i don't care) wireless works on this laptop. installed many programs, all without using the command line. not afraid of the command line. it's just not needed as often as many people would lead people new to linux to belive it is. and as for installing automatix, come on, you surely don't need the command line to do that.

---

### Post by arron on 2007-03-26
hehhe the prompt is how the people that have been around for a while know how to do it.  Some old schoolers refuse to learn how to do it threw the gui, and for some reason.  If you can use a prompt for everything, then full system admin is a remote ssh login screen.  As well sometimes it is simple to use a prompt, and is somewhat distribution independent.

And no, I don't think anyone has had a *perfect* install.  Im glad to hear you had no problems, hehe until you start to tweak.  If everything worked perfectly, then a lot of geeks would have nothing to do then.

Needed?  No.  Not for general use.  More advanced use?  More likely you will come to the dark side. Why?  Because the force is strong!

Damn now im a geek!

---

### Post by halitech on 2007-03-26
> **coollikestevie said:**
> yes i am so smart! i fixed it :P i typed the first command in wrong and it put all this **** into the sources.list file.. i just had to go and edit it.

thanks for flaming me for following a command line junkie... but u know he got those commands straight of the automatix website.

you missed the end quote didn't you ;)

been there, done that and thats the great thing about linux, simple screw up allowed you to learn how to fix your computer instead of just formatting and reinstalling :D

personally I love the command line but I started back in the days of DOS and hated how little windows would let you do with the gui so it was little problem for me to drop to the CLI but I'll try to point others to a gui if possible. it's all a matter of personal preference

---

