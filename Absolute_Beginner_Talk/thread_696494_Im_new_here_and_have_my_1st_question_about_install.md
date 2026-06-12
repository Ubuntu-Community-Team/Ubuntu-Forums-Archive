---
title: "Im new here and have my 1st question about installing programs"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by skozzy on 2008-02-14
I have had v7.1 Ubuntu installed for a week, I have tackled many issues on my own mostly networking related. Got it done, email is also working.

But having used Windows for years and this being all new to me I find I am stuck with access my own system.

My present problem is installing Sun Java, I downloaded an 18mb .bin file, opened the instructions on the Sun Java site about installing it, and the step I am stuck at:

The instructions say open a terminal and type SU, I do that and it asked for a password, I tried the password I use to log in after booting, I tried my username as a password, then the computer name as a password and even no password at all. But the responce is : su: Authentication failure

Can someone tell me where or what this password might be.

---

### Post by Gigidy5 on 2008-02-14
Thats something that happened to me a lot.


what happened for me is that I would have to type my password and then hit enter very quickly after typing it.

---

### Post by khensucat on 2008-02-14
My first question would actually be: Why not install java using Add/Remove programs or Synaptic? Installation and configuration would be automatic. Is there a specific reason you need to install from source?

---

### Post by skozzy on 2008-02-14
Well that didn't work for me, Any faster typing and my fingers will fall off

---

### Post by amingv on 2008-02-14
Doing

```
sudo apt-get install sun-java6-bin sun-java6-plugin
```
should be easier.

Reading this will help a lot too:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by skozzy on 2008-02-14
khensucat   - 

Um reason is I have no idea what you mean buy synaptic

I was just trying to follow the instructions on the sun java site

Remeber im am new and at present nothing is making sence and im moving along slowly with the learning curve

---

### Post by jan quark on 2008-02-14
either you open up the terminal 

system > accessories > terminal

and type this

```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

or you go to 
system > administration > synaptic

and type java into the search field and check the box to mark for installation and click on apply

---

### Post by skozzy on 2008-02-14
amingv - I get a reply saying it cant be found. The filename is jre-6u3-linux-i586.bin and was downloaded to my desktop from firefox

---

### Post by paydaydaddy on 2008-02-14
Try sudo rather than su.

---

### Post by jan quark on 2008-02-14
also check out this guide for java

[http://www.psychocats.net/ubuntu/java](http://www.psychocats.net/ubuntu/java)

and the whole site is a great starting point for beginners :)

---

### Post by amingv on 2008-02-14
> **skozzy said:**
> amingv - I get a reply saying it cant be found. The filename is jre-6u3-linux-i586.bin and was downloaded to my desktop from firefox

Run
```
sudo apt-get update
```

and then the code in my first post.

Also make sure you have extra repositories enabled:
[http://www.psychocats.net/ubuntu/sources#simple](http://www.psychocats.net/ubuntu/sources#simple)

---

### Post by khensucat on 2008-02-14
> **skozzy said:**
> khensucat   - 

Um reason is I have no idea what you mean buy synaptic

I was just trying to follow the instructions on the sun java site

Remeber im am new and at present nothing is making sence and im moving along slowly with the learning curve

That's ok. Click on "System", then, Administration, then "Synaptic Package Manager". In the field marked "Search", search for Java. Right click on Java 6, and accept the additional packages it wants to install. Click "OK" (or the equivilant it gives). You'll have to accept the liscence through a popup window. Then it should be set up for you.

That way, you'll learn you can search for any kind of program using Synaptic ;-)

Also, the command line instructions posted above do the same thing ;-)

---

### Post by mali2297 on 2008-02-14
> **skozzy said:**
> amingv - I get a reply saying it cant be found. 

You need to enable the **multiverse** repository, see here
[http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories](http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories)

---

### Post by oedha on 2008-02-14
how bout this........
go to system - administration - update manager
click check and if there's update...install them
then 
go to applications - Add/Remove
seacrh for java on "all available application"
you can pick some java there...:)

---

### Post by ibbill on 2008-02-14
as paydaydaddy said try  sudo then type the password and if your like me it surpised me it never showed up the password I typed was told type it and hit enter worked for me

---

### Post by mister_pink on 2008-02-14
To clear up any confusion about that "su" command, su by default makes you the superuser, root, for the rest of that terminal session or until you end it. The password it asks for is the root password. In ubuntu the root account is disabled, so to do things as the superuser you put "sudo" before the command (on the same line) and use your own password. If you need to do several things as root in an row, you can use "sudo su" or "sudo -i" to make yourself the superuser. In this case, however, I suggest you follow the other advice to just install it from the repo. 

To learn more, check out the wiki [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by hvard on 2008-02-14
if i'm not mistaken su account is disabled in Ubuntu by default. Instead you need to use sudo if you want to perform action that needs admin privileges. So to install your bin file you need to type sudo ./<filename>. But before that you need to make file executable by issuing command sudo chmod +x <filename>. If you'd like to login as root (and not issue sudo with each command) then issue command sudo -i. But please not that's a dangerous thing, as you inadvertently might harm your system.

> **skozzy said:**
> I have had v7.1 Ubuntu installed for a week, I have tackled many issues on my own mostly networking related. Got it done, email is also working.

But having used Windows for years and this being all new to me I find I am stuck with access my own system.

My present problem is installing Sun Java, I downloaded an 18mb .bin file, opened the instructions on the Sun Java site about installing it, and the step I am stuck at:

The instructions say open a terminal and type SU, I do that and it asked for a password, I tried the password I use to log in after booting, I tried my username as a password, then the computer name as a password and even no password at all. But the responce is : su: Authentication failure

Can someone tell me where or what this password might be.

---

### Post by skozzy on 2008-02-14
So far im not having any luck installing the latest sun java, Its obvious im missing something. I still have the bin file on the desktop screen called jre-6u3-linux-i586.bin I followed the current instructions and also followed the link to another site for help, but I still  cant install this, I would like to use the instruction on the sun java site, but the command SU still asks for a password and it won't accept my login password. The admin/synaptic package manager doesn't import or open or do anything with the file jre-6u3-linux-i586.bin

---

### Post by skozzy on 2008-02-14
well something worked but im not sure what, I opened the online game that uses java and instead of asking for the java plugin it began installing it. So im not sure what part of all this helped, but surely something has

---

### Post by p0k3r808 on 2008-02-14
You can create a specific password for su (super user) so that you can login to it and it will change your $ to a # and you wouldn't have to type sudo (super user do) before your commands.  

It is recommended you keep using sudo instead of creating a new password for su.  But to create a su password type in:


sudo su passwd



then enter your new super user password.

---

### Post by Miljet on 2008-02-15
Trying to install the jre-6u3-linux-i586.bin file from [www.java.com](www.java.com) WILL NOT work using the directions posted there. I fought with it for over two weeks and never did get it installed. If you read all the instructions, you will realize that the instructions do not cover Ubuntu or Firefox. It is much easier to use "sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts" from the terminal. When it asks for your password, use the same one you log in with.

---

### Post by oldos2er on 2008-02-15
> **skozzy said:**
> So far im not having any luck installing the latest sun java, Its obvious im missing something. I still have the bin file on the desktop screen called jre-6u3-linux-i586.bin I followed the current instructions and also followed the link to another site for help, but I still  cant install this, I would like to use the instruction on the sun java site, but the command SU still asks for a password and it won't accept my login password. The admin/synaptic package manager doesn't import or open or do anything with the file jre-6u3-linux-i586.bin

Ubuntu uses sudo, not su.

 Synaptic Package Manager will not use the *bin file you downloaded. Synaptic downloads files from sites called repositories, which contain files (or packages, as they're called), made specifically for Ubuntu. Whenever possible, you want to use Ubuntu's repositories first.

 I suggest you read [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) .

---

