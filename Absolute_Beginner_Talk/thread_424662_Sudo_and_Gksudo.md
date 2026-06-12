---
title: "Sudo and Gksudo"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by trishacupra on 2007-04-26
What's the difference between sudo and gksudo? Thanks.

---

### Post by zubrug on 2007-04-26
gksudo gives root admin privelages,

---

### Post by holdinout on 2007-04-26
Gksudo will bring up a graphic password screen whereas sudo will simply ask the password during a terminal session... I think... Other add please.

---

### Post by Seisen on 2007-04-26
You use gksudo for graphical apps like nautilus or firestarter if your running them from the terminal. If its not a graphical app. then you use sudo. They both do the same thing by giving you super user privileges.

---

### Post by trishacupra on 2007-04-26
Okay, so I've been using a desktop launcher with type:'Application in Terminal' and the command:'sudo nautilus'.

Is this good/bad? It 'works' - just worried if something bad is happening because of it that I can't see. Am I paranoid?

---

### Post by tman_ubuntu on 2007-04-26
> **trishacupra said:**
> Then what does sudo do? And which do you use for what?

gksudo brings up the GUI password entry dialog.  Sudo prompts for password at the commandline.

---

### Post by bobplano on 2007-04-26
sudo is just for terminal stuff, because for real graphical applications, i think sudo will crash. gksudo is used to run graphical apps as root where sudo is for commands where you don't need that  such as sudo apt-get update

---

### Post by trishacupra on 2007-04-26
> **tman_ubuntu said:**
> gksudo brings up the GUI password entry dialog.  Sudo prompts for password at the commandline.

So, it's not really a big deal about which you use?

---

### Post by Midgetmunky13 on 2007-04-26
sudo for command line, gksudo for the GTK-based GUI

im not this smart with this i just just looked on Google. i was wondering the diff too. hope this helps!

---

### Post by Seisen on 2007-04-26
Read this it will explain it better 

[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by trishacupra on 2007-04-26
> **bobplano said:**
> sudo is just for terminal stuff, because for real graphical applications, i think sudo will crash. gksudo is used to run graphical apps as root where sudo is for commands where you don't need that  such as sudo apt-get update

So, it does matter then? That seems logical.

---

### Post by holdinout on 2007-04-26
Ok, you would use Gksudo to bring up anything in a graphic form, ie. Synaptic, Thunar, etc. Sudo will be used in a command for a terminal only execution. T-man nailed it.

---

### Post by trishacupra on 2007-04-26
> **Seisen said:**
> Read this it will explain it better 

[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

Perfect!!! Psychocats to the rescue again.

---

### Post by gilda on 2007-04-26
sudo is for use in the terminal. Like if you want to run a command that you dont have permissions to for your user. 

gksudo is used if you want to open a graphical  application with permissions. 
Like if you wanted to edit a text file that you dont have privileges to say the /etc/X11/xorg.conf  file   
for example.

You can then in terminal or through your run box type gksudo gedit and it will open the application with root privileges so you may edit that file.

---

### Post by Midgetmunky13 on 2007-04-26
wow that sucks, i would have been the first to answer the post but by the time i found the info, ur question was answerd.o well at least i larned somthing.

---

### Post by trishacupra on 2007-04-26
> **gilda said:**
> sudo is for use in the terminal. Like if you want to run a command that you dont have permissions to for your user. 

gksudo is used if you want to open a graphical  application with permissions. 
Like if you wanted to edit a text file that you dont have privileges to say the /etc/X11/xorg.conf  file   
for example.

You can then in terminal or through your run box type gksudo gedit and it will open the application with root privileges so you may edit that file.

Okay, I understand it now. Cool.

Thanks for all the replies!

---

### Post by Seisen on 2007-04-26
Sounds a little familiar Gilda doesn't it?

---

### Post by gilda on 2007-04-26
LOL just a lil Seisen

;D

---

### Post by Patrick K on 2007-04-26
So where does gksu come in? I have to use gksu to run qjackctl from the menus. It will not launch with gksudo.

---

### Post by gilda on 2007-04-26
GKSu is a library that provides a Gtk+ frontend to su and sudo. It supports login shells and preserving environment when acting as a su frontend. It is useful to menu items or other graphical programs that need to ask a user's password to run another program as another user.

---

### Post by jingo811 on 2007-06-17
Nice explanation from Pshycocats I never realized that.
Gui apps= Gksudo, CLI apps= Sudo, 
ignore warning it's low priority......I think I got it now.

---

### Post by dondad on 2007-06-18
I am not positive that it caused the problem, but I have accidentally used sudo with graphic apps and had the system change my home directory to being owned by root, which cause boot problems as well as a host of others. I had to go in and fix all of the permissions. I have seen several other threads with the boot problem, and as far as I have been able to tell, most, if not all of them used sudo rather than gksudo for graphics applications.

---

