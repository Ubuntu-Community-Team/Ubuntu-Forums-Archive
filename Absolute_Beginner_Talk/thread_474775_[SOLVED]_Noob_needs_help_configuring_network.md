---
title: "[SOLVED] Noob needs help configuring network"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-06-15
attached is a quite elementary drawing of my current configuration. I can access the internet on the ubuntu box but I don't know where to begin on setting up the network in Ubuntu so i can share/transfer files between the machines. Any help would be much appreciated.

---

### Post by Mazza558 on 2007-06-15
> **ITdrummer said:**
> attached is a quite elementary drawing of my current configuration. I can access the internet on the ubuntu box but I don't know where to begin on setting up the network in Ubuntu so i can share/transfer files between the machines. Any help would be much appreciated.

I'd advise setting up your network on the PC connected to the netgear router. Then Ubuntu would be able to access your Windows Network straight away.

---

### Post by rufius on 2007-06-15
This tutorial might help: [http://zacbrown.org/tutorials/SAMBA-HOWTO](http://zacbrown.org/tutorials/SAMBA-HOWTO)

^^ It might be a bit weighty but it will work.

---

### Post by nymphaeles on 2007-06-15
There are two ways, a Windows share or a Samba share, you only need to go with one unless you're curious to do both.
You can set up a share in XP and the unbuntu machine will see it right away (boring).  Or you can set up Samba  server in the Ubuntu machine (now we're talking!  that's why you're here, right?) and have the XP machines connect to it.
Try a Samba tutorial and post you questions here.  It's truly simple and you'll proud of yourself!

---

### Post by ITdrummer on 2007-06-15
Sounds interesting, but i know nothing about it. What is samba? what does it do?

---

### Post by Bluecircle on 2007-06-15
```

sudo apt-get install samba
sudo apt-get install samba-common

```

It lets you network/share files between windows and linux computers.

---

### Post by ITdrummer on 2007-06-15
is that all it takes to install it? just those 2 lines of code?

---

### Post by Bluecircle on 2007-06-15
yeah pretty much. You can set it up by gonig to System -> Administration -> Shared Folders

---

### Post by Golyadkin on 2007-06-15
> **ITdrummer said:**
> is that all it takes to install it? just those 2 lines of code?


Yeah :) and people say Linux is hard.....tssk :D :D :D

---

### Post by ITdrummer on 2007-06-15
So i have another question.  When you do to the add/remove programs list in Ubuntu, where do the programs come from? are they already on the system? Why do you have to install them if they are? This all is a bit confusing, I'm sorry if that sounds like a dumb question but i just cant wrap my brain around just using a couple of lines of code to install an entire program.

---

### Post by Golyadkin on 2007-06-15
They are being downloaded on the fly from what are called 'repositories'. They are large libraries of installations programs, ready for you to use. They will give you the right version automatically.

---

### Post by Golyadkin on 2007-06-15
I will try to make it sound very simple:

When you type: "sudo apt-get install samba" you are kinda saying this to your computer:
> 
Hey computer, I wanna do something with programs. ( the "apt-get" part)
I want to install something. (the "install" part, this can also be "remove" to uninstall)
What I want to install is called "samba"  (the "samba" part, which is the name of the program)
Oh, and I know the administrator password, so I am allowed to install new things  (the "sudo" part)

The computer will think and check if "samba" is already installed. If it is not, it will look in a list of available programs if it exists there. If it finds it, it will look if there are other things you need to make the program work. These are called dependancies. If it finds them, it will install them if you don't have them installed yet. If not, it will merrily continue. 
Now it downloads the installer for the program you want ("samba") and all it's dependencies. It runs the installer automatically and informs you it is done.
Thats all, super simple.

Oh and btw, two lines of code? You can do it in one line like this ;) :
> 
sudo apt-get install samba samba-common

because after "install" you can type a whole list of programs you want, as long as you put spaces in between them.

---

### Post by bren on 2007-06-15
hi nympahaeles  and others

what would you recommend to allow work laptop (logged to domain i think) and home ubuntu box to connect ?

same as above or different.

ubuntu would be hard wired to wireless router
work laptop connected to router via wireless (only got one cat5 cable at home at mo)

[i have admin rights on the work laptop but not really allowed to install new software]

thanks
bren

---

### Post by ITdrummer on 2007-06-15
and using the 

sudo apt-get install samba

is the CLI version of:

Applications>>add/remove programs>>samba  ?

---

### Post by Golyadkin on 2007-06-15
Yes, exactly the same. The Applications > Add / Remove > samba actually runs the "sudo apt-get install samba" in the background, it just makes it look nice for you.

---

### Post by ITdrummer on 2007-06-15
awesome, thanks for your help

---

### Post by Golyadkin on 2007-06-15
You are welcome, I am glad to be able to help and make things a little more understandable. I come from the RedHat 4.0 time (in 1996) when you would rather stick a fork in your arm than install software in Linux :D  Linux has come a loooong way since then.

---

### Post by jaydee123 on 2007-06-15
> **Bluecircle said:**
> yeah pretty much. You can set it up by gonig to System -> Administration -> Shared Folders
I have tried setting up ubuntu with vista.
It finds windows workgroup but wont open files. 
Vista does not see it.
puzzled!!!!;)

---

### Post by Bluecircle on 2007-06-15
> **jaydee123 said:**
> I have tried setting up ubuntu with vista.
It finds windows workgroup but wont open files. 
Vista does not see it.
puzzled!!!!;)

I've only used it with XP and it worked fine. Never tried it on Vista.

---

### Post by ITdrummer on 2007-06-19
thanks for everyones help

---

