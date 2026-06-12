---
title: "How do I remove Gnome/Xubuntu?"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by Narcoleptic_Insomniac on 2006-10-12
Yea so I just installed KDE and its awesome, I really like it and I want to remove Gnome and KDE so what are the terminal command lines?

---

### Post by petri on 2006-10-12
The command lines you will find here: [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

### Post by dannyboy79 on 2006-10-12
you should learn to use gogle or even search our very own ubuntu forums, here you go. [http://ubuntuforums.org/showthread.php?t=157897](http://ubuntuforums.org/showthread.php?t=157897)

---

### Post by petri on 2006-10-12
> **dannyboy79 said:**
> you should learn to use gogle or even search our very own ubuntu forums, here you go. [http://ubuntuforums.org/showthread.php?t=157897](http://ubuntuforums.org/showthread.php?t=157897)

Have you tested them? Have you checked the site I linked to?  Or are some scriptkiddies creations better than try to learn CLI... :rolleyes: 

And yes, people should use Search and they will some day. But everyday there is new users who don't know about Search and besides, they do think their problem are very special.

---

### Post by aysiu on 2006-10-12
I wrote the link you posted, petri, and I think it's actually easier for new users than running a script.

After all, with the script, they have to do untar a .tar.gz and run the script. With my link, you can just highlight everything and paste the command into the terminal.

And, as you note--it's quite transparent... telling you everything that it's going to remove.

---

### Post by petri on 2006-10-12
> **aysiu said:**
> I wrote the link you posted, petri, and I think it's actually easier for new users than running a script.

After all, with the script, they have to do untar a .tar.gz and run the script. With my link, you can just highlight everything and paste the command into the terminal.

And, as you note--it's quite transparent... telling you everything that it's going to remove.

I know it's yours, I was just trying to be sarcastic. Yes, I know I shouldn't try moderate other users, the moderators do that. I just got irritetad because the guide I was linking to can people learn of and maybe get curious to learn more instead of running scripts they don't know nothing about. 

Though now I have to say I like Automatix. :rolleyes:

---

### Post by aysiu on 2006-10-12
I was agreeing with you about the script. I don't think it's necessary when you can just copy and paste in one command.

Automatix is a bit more complex than that and is worth scripting.

---

### Post by dannyboy79 on 2006-10-12
> **petri said:**
> Have you tested them? Have you checked the site I linked to?  Or are some scriptkiddies creations better than try to learn CLI... :rolleyes: 

wait, you call copying and pasting learning the cli????? At least the way I suggested they learn how to untar and run script which are both things they will definitely need to know regarding linux.

> **petri said:**
> 

And yes, people should use Search and they will some day. But everyday there is new users who don't know about Search and besides, they do think their problem are very special.

YEs, I did test it, I used it to uninstall Gnome from my Xubuntu box. ALso, the solution I referenced is better than Psychocats because his is more dynamic and faster.

Dynamic because it checks the meta packages for each version on load time.
Faster because it only tries to remove packages that are installed on your system.

---

### Post by gosh on 2006-10-12
> **aysiu said:**
> I wrote the link you posted, petri, and I think it's actually easier for new users than running a script.

After all, with the script, they have to do untar a .tar.gz and run the script. With my link, you can just highlight everything and paste the command into the terminal.

And, as you note--it's quite transparent... telling you everything that it's going to remove.

Any chance you will make an Edgy version of this page?
I have found it extremely usefull in Dapper. 
Thanx for that!:p

EDIT: when I try it on Edgy I get the following message when removing KDE-residu:
```
ome packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  openoffice.org-l10n-en-gb: Depends: openoffice.org-common (>= 2.0.4~rc3) but it is not going to be installedor
                                      language-support-en but it is not going to be installed
                             Depends: openoffice.org-common (< 2.0.5) but it is not going to be installedor
                                      language-support-en but it is not going to be installed
  openoffice.org-l10n-en-za: Depends: openoffice.org-common (>= 2.0.4~rc3) but it is not going to be installedor
                                      language-support-en but it is not going to be installed
                             Depends: openoffice.org-common (< 2.0.5) but it is not going to be installedor
                                      language-support-en but it is not going to be installed
E: Broken packages

```

---

### Post by PriceChild on 2006-10-12
> **dannyboy79 said:**
> wait, you call copying and pasting learning the cli?????Definately! considering the alternatives such as automatix and EasyUbuntu, simply looking at the code they are pasting helps them understand... its how i've got where i am today!

---

### Post by justin whitaker on 2006-10-12
Hey guys, this is not worth arguing over. Does it do the job? Yes. Good enough.

---

### Post by aysiu on 2006-10-12
I happen to be a big fan of copying and pasting, but I agree with dannyboy79 that you will learn a lot more by having to untar.

The tutorial I created is deliberately for not learning. Copy, paste, done.

---

### Post by thornomad on 2006-10-12
> **aysiu said:**
> The tutorial I created is deliberately for not learning. Copy, paste, done.

I don't understand the finer differences between apt-get and aptitude ... however, from that link you posted, it would seem that aptitude is a LOT easier to use.  

Why isn't that the "default" when recommending installations?  And, as someone who goes back and forth (apt-get, aptitude), is there a way to check which one I used before I undo it ?  Or, will trying to undo one I didn't use do nothing ? 

Thanks (I am learning?  See?)

---

### Post by aysiu on 2006-10-12
*aptitude* is smart, but sometimes it's **too** smart, which is why I used *apt-get* for that particular tutorial. I didn't want *aptitude* trying to guess what should or shouldn't be removed.

---

### Post by thornomad on 2006-10-12
> **aysiu said:**
> *aptitude* is smart, but sometimes it's **too** smart, which is why I used *apt-get* for that particular tutorial. I didn't want *aptitude* trying to guess what should or shouldn't be removed.

So you can interchange them ?  Run aptitude to install, then uninstall with apt-get?

---

### Post by aysiu on 2006-10-12
Yes, you can interchange them.

But if you want installed dependencies to uninstall when you remove an application, you must both install it and remove it with *aptitude*.

---

### Post by Ben Sprinkle on 2006-10-13
```
sudo apt-get -u ubuntu-desktop
```

---

