---
title: "Erm .. I just accidentally deleted /root."
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Steve_H on 2007-08-02
I know..I know, I'm a fool,  I've just accidentally removed the root home folder ( '$ sudo rm -r /root' ) and am not too sure what kind of repercussions this is going to have?

Is there a way I can re-create it, I'm still logged into the machine, so can use sudo etc?

Thanks!

Steve
(Feisty Fawn 7.04)

---

### Post by Smu on 2007-08-02
Uups... How in the earth did you manage doing that? I'm not sure what to do in your case. But I think you've deleted it for good, theres no undo for that. The /root folder is the home folder for the root user and can probably be recreated.

---

### Post by forestpixie on 2007-08-02
you might be better off - if you've got a seperate /home - to reinstall - at least it's quick.:) - just install to the / and don't touch /home.

If you've not turned off yet - don't until you're ready 

try and copy things you've had to change to get working - so you have copies of them 

In my case I always copy xorg.conf to a stick - it took me ages to sort out my tv out, so once i've reinstalled and got my nvidia ready I can just copy the old xorg back - I'm sure you get the idea

I would wait for a while see if anyone can come up with a magic pill 

But I think that sudo rm -r /root is pretty final - hopes to be proved wrong :)

---

### Post by Steve_H on 2007-08-02
I was trying to fix 'tilda' which broke this morning and failed to spot a space (had actually typed '$ sudo rm -r /root /.tilda' .

So you think I may need to re-install Ubuntu? dammt... means I may need to approach someone in IT with my tail between my legs...is a work computer. :S

---

### Post by ghanu on 2007-08-02
I dont know how far this would solve..but just give a try
boot from live cd and create a root directory in the respective harddisk partition 
and reboot...

---

### Post by chewearn on 2007-08-02
If you have a second ubuntu installation, you might be able to get away with simply copying the files/directories from it?

---

### Post by Steve_H on 2007-08-02
> **ghanu said:**
> I dont know how far this would solve..but just give a try
boot from live cd and create a root directory in the respective harddisk partition 
and reboot...
I've already managed create an empty root folder ($ 'sudo mkdir /root') as I'm still logged on, is this what you mean by 'create a root directory' or is there something different achieved when using the booting from the CD?

AstalaVista: I was kinda thinking something like that may be an option (how about copying my home dir into it), I could perhaps ssh into another machine and copy across files (.bash_history, .gnome. .gnome2, .etc) from root. Will have a look further.

Thanks for the input guys, is appreciated.

---

### Post by twhitney on 2008-05-22
I did this last week (by accident as well, and was quite stupid) I made a file by accident called ~ haha, and I was sudoed in, I typed "rm -rf ~" well, needless to say it took out the roots home directory...

There were no repurcusions that didn't allow me to login, to sudo, or even login as root, the /root just doesn't exist anymore... I was going to look into fixing it.

---

### Post by tamoneya on 2008-05-22
i think removing /root is just going to make it not possible to login as root.  You will still be able to sudo thought because you arent actually logging in in this case you are just getting root privileges.  Since in ubuntu you are very much discouraged from logging in as root this shouldnt be much of a problem.  The really serious thing is if you remove "/".

---

### Post by coffeecat on 2008-05-23
> **Steve_H said:**
> I've already managed create an empty root folder ($ 'sudo mkdir /root') as I'm still logged on, is this what you mean by 'create a root directory' or is there something different achieved when using the booting from the CD?


You could boot into the live CD and copy the contents of the live CD's root folder into the root folder on the HD. I should imagine that would do the trick, although I guess an earlier poster's comment that it would only matter if you wanted to log on as root.

I've just had a look in my Ubuntu root folder. There are a few hidden folders and files. The most important seems to be the .bashrc file.

---

