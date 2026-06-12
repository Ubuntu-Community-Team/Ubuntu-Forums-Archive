---
title: "Issue with Firestarter and maybe &quot;gsku&quot;"
date: 2005-09-29
forum: Absolute Beginner Talk
---

### Post by pmf on 2005-09-29
Hi.  

I installed Ubuntu this afternoon on a PII 333mhz computer and am very impressed so far, however, I have finally reached the first hurdle.  

I downloaded the Firestarter firewall from the Synaptic Package application, and it installed fine, but when I try to start it from the Applications menu, it keeps asking for the Root password.  Thing is - I don't remember setting a root password!  

I can start it using the sudo command and entering my password when it asks, but as soon as I close the Terminal Window, firestarter closes.  Entering my password in the prompt that appears doesn't help.  


Any ideas ? :confused:

---

### Post by Kapre on 2005-09-29
[QUOTE=pmf]Hi.  
I installed Ubuntu this afternoon on a PII 333mhz computer and am very impressed so far, however, I have finally reached the first hurdle.  
I downloaded the Firestarter firewall from the Synaptic Package application, and it installed fine, but when I try to start it from the Applications menu, it keeps asking for the Root password.  Thing is - I don't remember setting a root password!  
I can start it using the sudo command and entering my password when it asks, but as soon as I close the Terminal Window, firestarter closes.  Entering my password in the prompt that appears doesn't help.  
Any ideas ? :confused:[/QUOTE]

pmf - the root password is the password that you're using. Its the same password that you enter when you go to your synaptic. Unless you have 2 accounts that you've set up.

---

### Post by pmf on 2005-09-29
[QUOTE=Kapre]pmf - the root password is the password that you're using. Its the same password that you enter when you go to your synaptic. Unless you have 2 accounts that you've set up.[/QUOTE]

I don't think I've set up two accounts.  However, the password that works for Synaptic PM doesn't work.  Would creating an account "Root" work?  

I might just uninstall Firestarter and use Shorewall.  



Paul.

---

### Post by Master Shake on 2005-09-29
Try the password for the first user you set up with Ubuntu.  That's what I put in when prompted, and it works.

---

### Post by Mustard on 2005-09-29
I can only really reiterate what has been said by others.  The password that firestarter is asking for is your sudo password, not the root password.  Maybe you could try changing your login password for whichever account you have that has sudo admin privileges.

---

### Post by hub on 2005-09-30
what you can do instead is set up a root passwd :
sudo passwd root
New passwd:
then type the root passwd
and retype it.

it is not the "debian - sudo" way however.

The problem with that method is that the firestarter GUI you will have will be under root id and you may not be able to change any config for the rules with that GUI. (you will be still able to change them by adding those rules manually with sudo under  gnome-terminal)

I don't know yet how to modify that GUI ID problem, let you know if i find.

---

