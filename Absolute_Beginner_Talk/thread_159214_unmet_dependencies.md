---
title: "unmet dependencies"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by steffeo on 2006-04-12
Hi! When I run sudo apt-get on most programs, (f.ex ion3, gaim) I get the message : The following packages have unmet dependencies.

I though ubuntu automaticly checked dependencies and installed them.

Any help, thank you...

- Steffen

---

### Post by pbaehr on 2006-04-12
I'm not positive, but could it be that they are dependant on files that are outside of your enabled repositories?

Maybe it checked the dependencies but failed to find them?

Just a theory.

---

### Post by steffeo on 2006-04-12
I suppose that could be a reason... doesnt help much though? ion I can understand, gaim however is a very common program... I installed opera without a hitch...

---

### Post by pbaehr on 2006-04-12
Sorry. Gaim is preinstalled in Ubuntu so I never had to install it myself...

I looked into it a little more and it seems like I was correct in my theory. You need to add the repositories that have the files that gaim is dependent on in order to install it.

---

### Post by aysiu on 2006-04-12
Something's wrong with your repositories list.

Get a fresh one:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by steffeo on 2006-04-12
Thank you so much, I will try this now :)

---

### Post by steffeo on 2006-04-12
I'm sorry, this did not help much, I am still getting the same message...

---

### Post by pbaehr on 2006-04-12
What if you run
```

sudo apt-get update

```
after you've changed your sources and prior to trying to install it?

Edit: I just noticed that that is one of the steps in the guide aysiu gave you so you probably already did that. Sorry.

---

### Post by steffeo on 2006-04-12
Yes, it was in the guide, so I did that. It find every dependencie, and if I try to apt-get the dependencie, I get the same thing...

here is what I get when trying to apt-get amsn : 
1. line : amsn : Depends: imlib1 but it is not going  to be installed.
 and so it goes on for every dependencie...

I dont get this...

---

### Post by davebgimp on 2006-04-12
First let's make sure your repos are correct. back up your source list first:
sudo cp /etc/apt/sources.list sources.list_backup

Then go here: [http://ubuntuforums.org/showthread.php?t=92672](http://ubuntuforums.org/showthread.php?t=92672)

Open your source list:
sudo gedit /etc/apt/sources.list
or kdesu kate /etc/apt/sources.list since you're on kubuntu.

and replace what you have with the recommended repos in that link I posted above. Save and type:
sudo apt-get update

Now try and install gaim.

---

### Post by steffeo on 2006-04-12
Sorry, still the same message...

---

### Post by steffeo on 2006-04-12
I ran sudo apt-get upgrade -f , it downloaded a whole bunch of stuff... and now it works!

what does really the f switch do ?

---

### Post by aysiu on 2006-04-12
[QUOTE=steffeo]I ran sudo apt-get upgrade -f , it downloaded a whole bunch of stuff... and now it works!

what does really the f switch do ?[/QUOTE] From ```
man apt-get
``` > -f
--fix-broken
    Fix; attempt to correct a system with broken dependencies in place. This option, when used with install/remove, can omit any packages to permit APT to deduce a likely solution. Any Package that are specified must completely correct the problem. The option is sometimes necessary when running APT for the first time; APT itself does not allow broken package dependencies to exist on a system. It is possible that a system's dependency structure can be so corrupt as to require manual intervention (which usually means using dselect(8) or dpkg --remove to eliminate some of the offending packages). Use of this option together with -m may produce an error in some situations. Configuration Item: APT::Get::Fix-Broken.

---

### Post by steffeo on 2006-04-12
thank you so much for helping :)

---

