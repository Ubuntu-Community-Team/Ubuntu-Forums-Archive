---
title: "I somehow managed to install the wrong linux"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by BRUUUCE on 2007-08-14
i decided to take the plunge into linux. I bought a compaq presario SR1730Z. I checked out ubuntus site and it said there were no problems with this specific build. I couldn't burn the CD correctly, so I checked out this website:

[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

i chose automated process, which you can download here:

[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html).

when i restarted, i chose ubuntu from the three options i had (the other two were windows)

installed perfectly aside from the bad resolution that makes everything gigantic but everything works. connected to the internet yadda yadda. about 15 minutes in, i notice i dont see the ubuntu logo anywhere, noticed my browser is not firefox which i think ubuntu comes with, and a foot in the top left corner, not the ubuntu logo.

i wanted to install ubuntu server edition and i somehow managed to have a nonserver version of some flavor of linux. At the end of the installation, it asked what packages i wanted, i tried to choose: webserver package but hitting enter while highlighted over it didnt select it but continue with the standard installation.

i can follow the tutorial again and just follow the linux instructions but i dont want to end up with another linux install that's not ubuntu.

so where did I go wrong?
and the best route from here to install ubuntu server.

Thank you

---

### Post by Blutack on 2007-08-14
You are probably safer burning a fresh disc. Have you tried following these instructions?
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by ErusGuleilmus on 2007-08-14
Dang, I dont know what happened, sounds like you might have installed Debian and not Ubuntu. I can send you a 7.04 Server disc if you want, its gotta be faster then shipit.

---

### Post by Blutack on 2007-08-14
By the way, I think this is a candidate for "Funniest Thread Title Of August".
Or is that really sad?

---

### Post by ErusGuleilmus on 2007-08-14
I dont know, I consider Linspire to be a "wrong" Linux.

---

### Post by st33med on 2007-08-14
> **Blutack said:**
> By the way, I think this is a candidate for "Funniest Thread Title Of August".
Or is that really sad?

Nah, just a little sad. (OK, not really)

---

### Post by BRUUUCE on 2007-08-14
> **Blutack said:**
> By the way, I think this is a candidate for "Funniest Thread Title Of August".
Or is that really sad?

it is kind of funny. I was so thrilled to have the install go so well only to find out it's not the correct distribution. I believe I have debian.

> **Blutack said:**
> You are probably safer burning a fresh disc. Have you tried following these instructions?
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)


i followed the Mac OSX instructions exactly and it burned fine but it didnt load up as an ISO on winXP. i could only browse through the files.


i also tried with windows but not following  that tutorial so i guess that's next

---

### Post by bluenova on 2007-08-14
Sound like you just have a base system installed. Try running:

sudo apt-get install ubuntu-desktop

or

apt-get install ubuntu-desktop (if you see root@computername :~$)

---

### Post by mali2297 on 2007-08-14
I'm curious, which distro did you get?

Type this in the terminal to find out:
```

cat /etc/issue

```

---

### Post by Blutack on 2007-08-14
Makes a change from OMG!!! IT BROKE!!!

Debian is pretty nice and very powerful, but a bit more oldskool and missing some of the nice GUI convienience features of ubuntu.  If you are new I would recommend using the tools in the article I posted above (they'll work in Debian too!) to burn yourself a nice fresh ubuntu server disc.  By the way, is server what you definately want?
Normally, a server install doesn't have a GUI, you just get a command line.

---

### Post by bapoumba on 2007-08-14
@ BRUUUCE: so you did try a ubuntu netboot installation, didn't you? Have you checked there:
[http://ubuntuforums.org/showthread.php?t=427540]("http://ubuntuforums.org/showthread.php?t=427540")

If you have a foot somewhere on the screen, you may be with a gnome desktop, that's all.

Edit: after checking the link about burning an ISO, please look here for the server edition:
[http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")

Edit n°2: disregard my post, I had your thread for too long up in my browser before I replied. More posts were added in the mean time.

---

### Post by BRUUUCE on 2007-08-14
> **mali2297 said:**
> I'm curious, which distro did you get?

Type this in the terminal to find out:
```

cat /etc/issue

```

it gave me:
Debian gnu/linux 4.0 \n \l

> **bluenova said:**
> Sound like you just have a base system installed. Try running:

sudo apt-get install ubuntu-desktop

or

apt-get install ubuntu-desktop (if you see root@computername :~$)

tried this, it said: "user is not in the sudoers file. This incident will be reported."  maybe i have to be logged in as root? how do i even do that, i tried to switch users but it wouldnt let me login as root.


after all this, i will heed the suggestion that server is probably something i should hold off on.

---

### Post by bluenova on 2007-08-14
Well looks like you ended up with debian, so my advice won't help. Really strange how that happened though, if you had an option of Ubuntu or Windows when you rebooted.

---

### Post by bwtranch on 2007-08-14
I went to my other box that has Mandriva on it to try to figure your problem out. It's been so long since I used that thing! It doesn't have apt on it either. To become root it's su -

---

### Post by p_quarles on 2007-08-14
Debian *does* have apt (they invented it, after all). But it does not automatically create a sudoer from the first user. 

Did you set up a root password when you installed? If so, you'll be able to log in as root using "su."

---

### Post by mali2297 on 2007-08-14
> **BRUUUCE said:**
> it gave me:
Debian gnu/linux 4.0 \n \l


Looks like you've got Debian Etch which is the latest stable version. (As I understand it that means more stable than any ubuntu version.) Good for you! :)

I don't know if I can help you but I will follow this thread with great interest.

---

### Post by BRUUUCE on 2007-08-14
> **p_quarles said:**
> Debian *does* have apt (they invented it, after all). But it does not automatically create a sudoer from the first user. 

Did you set up a root password when you installed? If so, you'll be able to log in as root using "su."

logging in as su did not work. however, i just tried root terminal and it said the ubuntu packages were not found. (tried both ways suggested)

burning the cd as we speak!

---

### Post by BRUUUCE on 2007-08-15
last update for this matter:

cd install still didn't work so i got lubi and installed over the net. and WOW, looks so pretty! haha. resolution is fixed now too.

thanks everyone for the help with this crazy circumstance. i still have no idea how it happened, but everything is fine now

---

### Post by Caffeine_Junky on 2007-08-15
heheheh,  this thread put a smile on my face ...glad everythin worked out for ya Bruuuce..    welcome aboard!

ps: *..hang on to that Debian installer mate,  you might wanna check it out some time.  ...sometimes the wrong one can be the right one :-p *

---

