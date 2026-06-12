---
title: "Trouble with Azureus"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by NeoRc on 2006-11-12
I just installed edgy in a few days ago. I found lots of applications had been added to the main server repository, like sun-java, like azureus, like acroread. I used to install them manually, but now I decide to install them from repository.

But then I got into some troubles. I found azureus cannot work correctly, it cannot minimize to sys-tray. Actually, it's no icon of the azureus in the sys-tray, when i click the "X" button, the app shutdown. Then I restart the azureus, I found the app doesn't really shutdown, It's just get hidden.

I go to the azureus website and download the latest version, it works good. Did I miss something, or the app on the repository still has some bugs?

---

### Post by allix on 2006-11-12
I had the same problem. Uninstalling the gij or gij-4.1 packages seem to help. Maybe there is some sort of conflict between gij and Suns java-vm.
Right now I'm running Azureus 2.5.0.0 downloaded from their website on sun-java5-jre. Works great.

---

### Post by tschaboo on 2006-11-30
i removed the gij and gij-4.1-packages but it didn't help. i really want to avoid installing anything manually. any idea?

---

### Post by aresgoddess on 2006-12-03
I ran the top command in the terminal, and saw that the gij-4.1 was eating up more than 50% of CPU. I removed one of the packages of gij, and now it runs a lot smoother. =) yay!

but what is sun-java5-jre? when i removed gij, the package manager had that marked as an upgrade, but i didn't mark it...

---

### Post by Jeproks on 2006-12-03
Hi guys.  Seeing how your all trying to figure out azureus...this might help...if you search azureus in Synaptic Package Manager, you'll notice there are two versions, one compiled for gcj or something, and one without the gcj.  Furthermore, if you search for java, you'll notice there are also two versions, the one with the g-string (hahaha), and the one without.  You must use the corresponding azureus files for the java version you are using.

The best way to get azureus running is if you first install java and then azureus, not the other way around, and the easiest way to do this is through the repos with Synaptic.  I recommend you install java first with Synaptic, then Apply, then install azureus.  From there you guys should be able to take it from there provided your network connections are configured properly.  To test it, run the NAT test in Azureus--->Tools.  If it connects your good to go.  If it doesn't, you might have a firewall up.  Before you start trying to figure out firewall settings, just try to disable it for a while, download/upload something...see if azureus works properly.  If it does, feel free to set up firewalls at your own risk.  Then post your results here.  :) 

After getting the hang of using synaptic, things will be a snap.  Also, if you guys want to make sure the programs in the repos are the latest versions, google them.  Hope this helps.  


Jeproks
Signature Not allowed by Keyboard.  hehe.

---

### Post by magiceraser06 on 2006-12-06
I too am having problems with Azureus. Worked great before, but now it won't even load. and when I got into terminal to try and load it, it says there is no such command.

also, its it installed. I used automatix and then synaptic then apt-get... still won't start up.

HELP!!

---

