---
title: "Ubuntu Newbie root vs. sudo question"
date: 2005-07-05
forum: Absolute Beginner Talk
---

### Post by aa33 on 2005-07-05
I've recently moved to Ubuntu from suse. It looks great so far. The thing is that I have been used to root user (for occasional config. changes) and limited user accounts for normal everyday use. With Ubuntu I get using sudo or su, but because sudo can be run with a limited user password as a limited user, it worries me that if the password of a limited account was breached (provided it was one in the sudoers file), sudo could be run and root privilages could be expoited. Could someone shed some light how this is more secure than other distros that use root and limited accounts only? Or please explain to me what is going on coz I might have got the wrong end of the stick...! (newbie)
Many thanks,

---

### Post by sapo on 2005-07-05
if you want root.. just use the root terminal:

Applications -> System Tools -> Root Terminal

You can enable root too.. but thats not a good idea.. just get used with the root terminal and you be fine  :grin:

Edit: i didnt read everything  ](*,) 

Btw.. i think that if somebody tries to hack your pc, he is gonna try to login as root.. for me is far more difficult to "guess" your normal user and password, than to try cracking into your root account...

But a lot of people say the opposite  :roll:

---

### Post by knewbix on 2005-07-05
I asked a [vaguely similar question](http://www.ubuntuforums.org/showthread.php?p=241431#post241431) last night. I think it all boils down to the fact that root password is no harder to crack than the everyday user password. Why have two passwords? I quote LordHunter317 here:

"[I]The core issue comes from the fact that having two accounts isn't inherently more secure than one, and having an account that's privileged all the time is bad.

With sudo, you're only privileged when you run a command with sudo. Everything else is unprivleged. That's the gain. It saves you from the headache of having two accounts.[/I]"

I am still getting my head around the whole thing really, because Kubuntu works differently from all the other distros I've tried, but hopefully that helps,

---

### Post by aa33 on 2005-07-06
Many thanks. I see. Good points.

Since yesterday when I posted this, i've been getting the hang of the sudo system. You're right,it is pretty good once one gets the hang of it. Maybe an explanation during the installation procedure to warn that this is the way things are done on ubuntu? Would save a lot of ubuntu newbies like myself getting temporarily confused, i think.
Thanks once again.
 O:)

---

### Post by GrootBrak on 2005-07-06
[QUOTE=sapo]if you want root.. just use the root terminal:

Applications -> System Tools -> Root Terminal

You can enable root too.. but thats not a good idea.. just get used with the root terminal and you be fine  :grin:

QUOTE]

I for one cannot open the Root Terminal. I get that "spinning disk" in my cursor and after a while things are back to what it was. The only way I can become root is through the terminal window, and change there to root. No root terminal for me. Been griping about it in other posts as well. 

The sudo thing is a PIA if you want to click and drag files, change user privalges or ownership etc etc. I have to physically look up my files in the GIU, then type in the path to it in the command line, else I cannot do a single thing with it, and that includes saving a just edited file. Example. I Open a picture with Gimp. Edit it, and when it comes to saving it, you "are not the owner... yada yada yada" comes up. Too late you discover the fact. So save back to your userfile, then change ownership via command line and copy file back to its original location.(Overwrite) At least that way I did not loose any changes I made to the pic.

---

