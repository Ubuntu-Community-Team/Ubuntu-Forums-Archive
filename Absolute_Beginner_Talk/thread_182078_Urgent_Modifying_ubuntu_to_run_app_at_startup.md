---
title: "Urgent: Modifying ubuntu to run app at startup"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by usr1 on 2006-05-25
Hi, I have ubuntu installed at startup and have installed a GUI based app on it. I would like ubuntu to not start GNOME t startup but rather start my app so that it looks like the OS is booting into my app. How can i do this. Do i just need to modify the .profile. Pls let me know.

---

### Post by neoflight on 2006-05-25
[QUOTE=usr1]Hi, I have ubuntu installed at startup and have installed a GUI based app on it. I would like ubuntu to not start GNOME t startup but rather start my app so that it looks like the OS is booting into my app. How can i do this. Do i just need to modify the .profile. Pls let me know.[/QUOTE]

did u install the application to run in gnome? would you please provide more info on the kind of application you have installed? what does this application do?

---

### Post by redistributer on 2006-05-25
What do you mean you don't want it to start gnome......
Does the GUI based app run in gnome, if so you have no choice but to load gnome first and then load your app automatically in gnome / to do that simply go to 
system --> Preferences --> sessions click on the startup programs tab and add the program to the list.

Hope this helps

-Red

---

### Post by usr1 on 2006-05-25
Its a basic windows emulator , that i installed from an rpm using alien. I dont want to have to wait for gnome to start up and then click on the icon to start it  up. I want it to start along with the boot and gnome to not start up. For eg. when we install the base ubuntu install, we come with a prompt for login/pass right..I want the emulator to start right from that point. I know I could just install a windows theme :), but there is a reason i want to run this app instead.

---

### Post by Clay85 on 2006-05-25
[Sarcasm]
omg liek dis iz toatalie live or deth EMERGANCY URGANT!! ZOMG!!1eleven@!```
[/Sarcasm]

H@x0r

What you are saying is you want to create your own Gnome/KDE/XFCE type GUI (evidently windows based)?

I have no idea how to do that.

---

### Post by usr1 on 2006-05-25
Actually its for a project, im trying to complete by tomorrow..hence the urgent. No need for the sarcasm folks ..

---

### Post by usr1 on 2006-05-25
It appears that this can run from a cygwin type environment too... So, i would assume it can run independent of gnome from the command prompt. I will need to try that, but does anyone know, what config i need to change to suppress the gnome startup after boot

---

### Post by Clay85 on 2006-05-25
I usually reserve the word 'urgent' for life or death situations. If you browse the forums you'll notice almost no one uses the word urgent in their headline. 

Lack of preperation on your part, does not an emergency on my part make.

Next time just explain the urgency inside the post, not in the headline. I bet you'll get more responses.

---

### Post by Clay85 on 2006-05-25
Try choosing 'last session' under the session manager. I have no idea if that will work, but it makes sense to me.

---

### Post by steve.horsley on 2006-05-25
Try following the trail that leads from man startx. This references xinit and xinitrc. I had a quick look, but got lost after that.

---

### Post by redistributer on 2006-05-25
just edit /etc/inittab in the line that says
# The default runlevel.
id:5:initdefault:

change that to this

# The default runlevel.
id:3:initdefault:

This will boot you into command prompt only

---

