---
title: "How to use command-line interface (CLI) for the login screen ONLY"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Ghuloomo on 2008-02-25
Hey, I want to be able to make my login screen (where I enter my username and password) only a terminal like type. No GUI, only writing my username then password and then logging in to the GNOME interface.

Notice, that I want the Ubuntu itself having a graphical user interface, **but only the login screen without any**. Is that possible?

The first days I installed Ubuntu, I unchecked "Graphical Login Manager (gdm)" from System -> Administration -> Services thinking this is the one I need, then I got restarted with a command line that I guess made my whole system a CLI. And I couldn't get back to the GUI coz I didn't know anything about terminal codes, and how to get GNOME desktop environment back. I was like entering my name, then my password and nothing happens, then had to make a fresh new install of Ubuntu.

---

### Post by justleen on 2008-02-25
the way you did it is fine... you just have to make the system start X for you.

once logged in, you can type "startx"

if you alway want X to start after login, add startx to your .profile (/home/users/,profile)

---

### Post by Ghuloomo on 2008-02-25
Then I can enter my username and password and login to the GUI? Are you sure about that? No tircky things will come across? I'll try to do that, if it worked, I'd want you to show me how to add it to the .profile file please.

Thanks justleen

---

### Post by SOULRiDER on 2008-02-25
> **justleen said:**
> the way you did it is fine... you just have to make the system start X for you.

once logged in, you can type "startx"

if you alway want X to start after login, add startx to your .profile (/home/users/,profile)

I beleive the line should be added to your ~/.bashrc file, but i may be wrong.

---

### Post by JPotter on 2008-02-25
Another option for the lazy: Log in as you did, without the gui. then input:

```
sudo /etc/init.d/gdm start
```

this will start GNOME.

---

### Post by roaldz on 2008-02-25
> **JPotter said:**
> Another option for the lazy: Log in as you did, without the gui. then input:

```
sudo /etc/init.d/gdm start
```

this will start GNOME.

Wouldn´t that start the login manager (GDM)?

---

### Post by Ghuloomo on 2008-02-25
I disabled  "Graphical Login Manager (gdm)" from System -> Administration -> Services, and as justleen told me i typed "startx" in the command-line after rebooting, that toke me directly to my username, without even prompting me to enter my password. Also I have other usernames for other members of the family, so how they can login with their own username?

Let me clarify more, and thanks in advance.. What I am expecting is to reboot my pc, then see like "Enter username:"and i type it, then the password, and then login to Gnome like usual. I want all this without any fancy looking login screen; only the terminal.

Trying to save some resources by cutting of what is not needy.

---

### Post by roaldz on 2008-02-25
> **Ghuloomo said:**
> I disabled  "Graphical Login Manager (gdm)" from System -> Administration -> Services, and as justleen told me i typed "startx" in the command-line after rebooting, that toke me directly to my username, without even prompting me to enter my password. Also I have other usernames for other members of the family, so how they can login with their own username?

Let me clarify more, and thanks in advance.. What I am expecting is to reboot my pc, then see like "Enter username:"and i type it, then the password, and then login to Gnome like usual. I want all this without any fancy looking login screen; only the terminal.

Trying to save some resources by cutting of what is not needy.

Ah, you can configure gdm (Administration --> Login window) to be more light-weight:)

Go to local, and pick ¨plain¨ for style. This should make it more lightweight. 
I´m not so sure about how many resources gdm eats when you are in gnome, I think it´s not much, especially with a non-themed login window.

Hope it helped,

Roald

---

### Post by Ghuloomo on 2008-02-25
> **roaldz said:**
> Ah, you can configure gdm (Administration --> Login window) to be more light-weight:)

Go to local, and pick ¨plain¨ for style. This should make it more lightweight. 
I´m not so sure about how many resources gdm eats when you are in gnome, I think it´s not much, especially with a non-themed login window.

Hope it helped,

Roald
I'm already using the plain one :p 

but need to make it like terminal.. are you up for the challenge? ;)

---

### Post by Dr Small on 2008-02-25
How about removing executable permissions from gdm:
```
sudo chmod -x /etc/init.d/gdm
```

And then when the system reboots, it should not be able to launch GDM.
Now, to get back to the desktop, after you login, type:
```
xinit gnome-session -- :0 vt7
```

And that should start an X session on Display 0, Virtual Terminal 7, while launching gnome-session.

Dr Small

---

### Post by Ghuloomo on 2008-02-26
> **Dr Small said:**
> How about removing executable permissions from gdm:
```
sudo chmod -x /etc/init.d/gdm
```

And then when the system reboots, it should not be able to launch GDM.
Now, to get back to the desktop, after you login, type:
```
xinit gnome-session -- :0 vt7
```

And that should start an X session on Display 0, Virtual Terminal 7, while launching gnome-session.

Dr Small
Thanks for it, but still I'm not getting what I am looking for

---

### Post by roaldz on 2008-02-26
Removing execute permissions from /etc/init.d/gdm is not the right way. That file is meant to be executable. Disable it from starting at boot like Ghuloomo did is the right way. If that line
```
xinit gnome-session -- :0 vt7
```starts the right gnome session, you must append it in ~/.profile, that way it will be executed every time you login from terminal.
This file is located in every user´s homedir, so you´ll have to modify all .profile´s to achieve the right result.

Roald

ps. I honestly think it´s not going to be much of a difference. What are the system´s specs? (especially RAM).

---

### Post by Ghuloomo on 2008-03-08
> **roaldz said:**
> Removing execute permissions from /etc/init.d/gdm is not the right way. That file is meant to be executable. Disable it from starting at boot like Ghuloomo did is the right way. If that line
```
xinit gnome-session -- :0 vt7
```starts the right gnome session, you must append it in ~/.profile, that way it will be executed every time you login from terminal.
This file is located in every user´s homedir, so you´ll have to modify all .profile´s to achieve the right result.

Roald

ps. I honestly think it´s not going to be much of a difference. What are the system´s specs? (especially RAM).
I'm having 512 RAM

---

### Post by louieb on 2008-03-08
> **justleen said:**
> the way you did it is fine... you just have to make the system start X for you.
once logged in, you can type "startx"
if you alway want X to start after login, add startx to your .profile (/home/users/,profile)

He is right. You probably got confused whey saw the line 
```
Running local boot scripts (/etc/rc.local)
```You need to press <enter> at this point.
        > Then I can enter my username and password and login to the GUI?
Not quite. After pressing enter you will get a login prompt asking for the user name.   After entering your user name and password. You will be logged on to a command line tty. You can run anything on your system now that doesn't require a GUI.

If you want a GUI then you would enter ```
startx 
```Log in managers like gmd, kdm and xdm are there for a reason.  To make it simple for non tech type people to login.  
Don't know how much it would save to not run one. But the lightest of the 3 is xdm. 

If you really want to save on resources you would need to do a custom install and don't run Gnome or KDE. Use fluxbox or one of the other lightweight window managers. Then the savings would be real and you could feel them. Its most noticeable on low powered system.
:guitar:   [Installation/LowMemorySystems - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

---

