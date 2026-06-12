---
title: "Monitor Problem- Cant see ubuntu"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by harrington on 2006-12-27
I am new to linux and Ubuntu. I have a Intel dual pc with xp on primary drive. I have a partition of 100gb off of primary. I am able to boot from the disc and see the welcome screen. When entering ubntu it seems to load I see it loading. The bar goes back and forth, then  just before  it looks like its done, the monitor does not display anything and goes into a standy mode. I hear an welcome sound then see nothing. Is this a driver issue?? I am just confused and have not found anyone else posting about this. I have the latest version burned as image on cd.

---

### Post by harrington on 2006-12-27
I have ati graphics card with LCD monitor

---

### Post by harrington on 2006-12-27
Anyone know how to fix this?

---

### Post by Jorge32 on 2006-12-27
A similar thing happened to me with a Matrox MGA200  video card, and I needed to install the MGA driver adn reconfigure it, if not I tried with a lower resolution and range by typing ctrl+alt+F4 in the black screen, then entering my username and password and then

```
sudo dpkg-reconfigure xserver-xorg
```


Maybe your problem is by someting like that, I hope this is useful information for you

---

### Post by harrington on 2006-12-27
Sorry where would I put this? And would this have to do with the refreh rate. Its a samsung monitor lcd with ati1300 I believe

---

### Post by harrington on 2006-12-27
ati x1300. do I need drivers??

---

### Post by Jorge32 on 2006-12-27
just type it if you can see something by typing at the same time ctrl+alt+F4 , a bunch of configuration options will appear, and I personally don't know anything about your hardware, for your monitor the range should be written in the monitor documents, but maybe you would like to try first searching about your problem, I've seen there's a lot of threads abaout ATI problems, try  clicking here in your browser search, and something like ATI 1300 or something like that. Good luck

---

### Post by harrington on 2006-12-27
Any other suggestions? I dont understand how to edit the xconf file. I am new to linux.. please help

---

### Post by Jorge32 on 2006-12-27
excuse me, maybe I wasn't too clear, The only thing that I can think of doing now is that.
well if everything works after typing at the same time ctrl+alt+F4 on the black screen should send you to a screen with letters. There it would be asking for user, type the username you created while installing Ubuuntu, and then the password you made for it ( the password won't appear, but yes it is tyoing it) then enter. After that something should appear with your username and the name of the computer. For example in my case it appears: jorge@ubuntu:~$
then there type the following:
```
sudo dpkg-reconfigure xserver-xorg
```
and type again your password if it asks for it.
With this it should appear the configuration. 
I hope to be more clear this time.

---

### Post by jonathan.lees on 2006-12-27
If you press CTRL + ALT + F4 do you get a screen that prompts you to login?

---

### Post by Jorge32 on 2006-12-27
If you aren't loged in, yes. It changes the screen  into a terminal. If you are already logged in, you will be able to type commands as your user

---

### Post by harrington on 2006-12-27
I have not installed the program yet, I was trying to use it as  a live cd and boot off the cd so i could try it

---

### Post by Jorge32 on 2006-12-27
Uhm, maybe if you have problems with the live cd use the alternate cd, of Ubuntu. But if what you was trying is to boot Ubuntu from the CD I don't know well if it can be done, and how to do it
here is the link for downloading the alternate cd
[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)

---

### Post by harrington on 2006-12-27
What do you recomend 

Ubuntu 6.06 LTS ( is that the second CD dapper)

or alternate setup. What is the difference?

---

### Post by Jorge32 on 2006-12-27
Ubuntu 6.06 is one, and the alternate version is 6.10 for installation in different machines, for example the ones that have less than some amount of ram memory ant higns like that

---

### Post by harrington on 2006-12-27
Anyone else know whats going on and how to fix it. I am a newbie and need steps, Very frustrating, I appreciate the help!

---

