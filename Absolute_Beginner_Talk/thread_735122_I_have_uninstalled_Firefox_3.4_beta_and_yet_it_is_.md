---
title: "I have uninstalled Firefox 3.4 beta and yet it is still there."
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by boriquajake on 2008-03-25
I recently installed the Firefox 3.4 beta and I thought it was pretty cool but I am not ready to make the switch. Anyway, I went back into synaptic and marked it for complete removal and applied the changes. I also marked Firefox 2.0 for re-installation at the same time. Anyway, even after doing this the only firefox that comes up is the beta and I can't find the good ol' Firefox 2.0 to show up. I am dumb.

---

### Post by days_of_ruin on 2008-03-25
try removing firefox 3 and adding firefox 2 in separately,

---

### Post by boriquajake on 2008-03-25
> **days_of_ruin said:**
> try removing firefox 3 and adding firefox 2 in separately,


I did and no dice.

---

### Post by boriquajake on 2008-03-26
OK, I have gone into synaptic and marked firefox 3 for complete removal. After watching the system go through the process of removing it I then click on the generic Firefox icon that is under applications>Internet and lo and behold up comes the same damn Firefox 3 beta. What the heck am I doing wrong?

---

### Post by JeffoOfMetal on 2008-03-26
Dude, just run FF3 Beta. It does the same things as FF2 and probably works better. You're going through all this hassle to get an OLDER version of Firefox.

---

### Post by boriquajake on 2008-03-26
> **JeffoOfMetal said:**
> Dude, just run FF3 Beta. It does the same things as FF2 and probably works better. You're going through all this hassle to get an OLDER version of Firefox.

I like the beta but I can't install the google toolbar that I love to use, and it is buggy and weird, but thanks for the helpful tip.

---

### Post by stchman on 2008-03-26
> **boriquajake said:**
> OK, I have gone into synaptic and marked firefox 3 for complete removal. After watching the system go through the process of removing it I then click on the generic Firefox icon that is under applications>Internet and lo and behold up comes the same damn Firefox 3 beta. What the heck am I doing wrong?

Try this:

```
sudo apt-get autoremove firefox3
```

I am assuming that the name of the package is firefox3.  If not substitute the real name for firefox3.

The autoremove removes all unused dependencies.  After that remove the residual config in Synaptic.  Also use GTKOrphan to clean up your Ubuntu.  I also recommend the following commands to clen your Ubuntu installation.

```

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

```

After that your install will be clean.

---

### Post by LowSky on 2008-03-26
try deleting the .firefox folder in you home folder that should do it.

you will need to hit ctrl+h to see hidden files

---

### Post by Oldsoldier2003 on 2008-03-26
> **LowSky said:**
> try deleting the .firefox folder in you home folder that should do it.

you will need to hit ctrl+h to see hidden files

```
which firefox
``` will also help you be sure that firefox isn't installed again someplace strange that doesn't comply with the packaging standards and is fooling apt.

---

### Post by boriquajake on 2008-03-26
OK I did that, thank you for the help. Now, I need to know how to get Firefox 2.0 back on there. I installed it from synaptic but now how do I get it to start up?

---

### Post by Oldsoldier2003 on 2008-03-26
type firefox in a terminal and it should configure and run

---

### Post by iansane on 2008-03-26
should show up in applications>internet. right click and add to panel

---

### Post by boriquajake on 2008-03-26
OK, this is freaking weird. I followed the instructions to completely remove all of Firefox 3.4. I then went back into synaptic and selected Firefox 2.0 for installation. Once that was done I went into application menues and put Firefox back in the list of available apps. Anyway once that was done I went to applications>Internet>Firefox Web Browswe and the freaking 3.4 beta comes up.

---

### Post by boriquajake on 2008-03-26
> **Oldsoldier2003 said:**
> type firefox in a terminal and it should configure and run

I do that and the beloved 3.4 beta comes up. What the freak?

---

### Post by Oldsoldier2003 on 2008-03-26
> **boriquajake said:**
> OK, this is freaking weird. I followed the instructions to completely remove all of Firefox 3.4. I then went back into synaptic and selected Firefox 2.0 for installation. Once that was done I went into application menues and put Firefox back in the list of available apps. Anyway once that was done I went to applications>Internet>Firefox Web Browswe and the freaking 3.4 beta comes up.

are you running hardy? here is a thought. Uninstall FF and then install FF2 from the FFsite. then go in and lock the version in synaptic.

---

### Post by iansane on 2008-03-26
after uninstalling, do a search in the search console for firefox* in the entire system. You will see that there are files scattered all over if you do it before uninstall. Check to see if anything is left behind and then use gksudo nautilus or sudu in terminal to remove them before the fresh install.

Any danger in deleting anything with firefox in the name?

---

### Post by boriquajake on 2008-03-26
> **Oldsoldier2003 said:**
> are you running hardy? here is a thought. Uninstall FF and then install FF2 from the FFsite. then go in and lock the version in synaptic.

I am running Gutsy.

I am completely confused. In synaptic FF 2 and  and FF3 appear to be separate apps. In other wors I don't see how to accomplish what you are talking about with the forcing the version I want. Anyway, I have no idea what I am doing.

---

### Post by boriquajake on 2008-03-26
I don't care if the beta version is still there on my system somewhere, you know,  I just want to be able to use freaking FF2.

---

### Post by Oldsoldier2003 on 2008-03-26
> **boriquajake said:**
> I am running Gutsy.

I am completely confused. In synaptic FF 2 and  and FF3 appear to be separate apps. In other wors I don't see how to accomplish what you are talking about with the forcing the version I want. Anyway, I have no idea what I am doing.

once you've installed ff2 go into synaptic select it and do lock version from the menu

---

### Post by boriquajake on 2008-03-27
I don't know if I am now changing the original topic too much and this needs to be reposted by a moderator but I am to the point now where I need to start completely fresh with my browsers. I want to completely remove both Opera and Firefox. Firefox because I since I tried out the 3.4 beta I can't get back to version 2 and Opera because since I tried out the 9.5 beta that is buggy as hell too. I thought that I knew how to remove apps and lock versions and all crap using add/remove and synaptic package manager but this stuff is freaking killing me. I even downloaded  Firefox 2.0 from the mozilla site but I don't know how to install an ap that I didn't get from synaptic.

---

