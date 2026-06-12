---
title: "gDesklets sidebar"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by Noctiferis on 2007-11-05
Really sorry for this one.. but couldn't find the answer in other posts..
I've seen lots of sceenshots with a sidear on their desktop saying they use gdesklets but I can't find the gdesklet in the list.. how do they do it??
thx

---

### Post by bump_ on 2007-11-05
Run this code in the terminal to get it

"sudo apt-get install gdesklet"

---

### Post by esoxLucius4 on 2007-11-05
> **bump_ said:**
> Run this code in the terminal to get it

"sudo apt-get install gdesklet"


Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gdesklet

what to do now?

---

### Post by bump_ on 2007-11-05
Oops. I forgot the s

sudo apt-get install gdesklets


sorry about that.

---

### Post by Noctiferis on 2007-11-05
ok so I do that- open the manager but I can't find the sidebar... does it have a weird name?

---

### Post by bump_ on 2007-11-05
just type **gdesklets **into the terminal and look in your tray. From there you can add and remove things from your desktop.

---

### Post by travis31 on 2007-11-05
@Noctiferis
Even I could not find any sidebar for gDesklets. You could try Screenlets, which provides similar functions and has a sidebar (you will need a compositing manager like compiz though).

---

### Post by Noctiferis on 2007-11-05
sorry what do you mean by tray.. I can get to all the gdesklets but I can't find the sidebar one! the only thing I can see is sidecandy style stuff.. but it doesn't look like tho one on the screenshots I've seen

---

### Post by santiagoward2000 on 2007-11-05
> **travis31 said:**
> @Noctiferis
Even I could not find any sidebar for gDesklets. You could try Screenlets, which provides similar functions and has a sidebar (you will need a compositing manager like compiz though).

Travis is right. I haven't seen a sidebar for Gdesklets. But [Screenlets]("www.screenlets.org") have a really cool one!
[http://www.gnome-look.org/content/show.php/Sidebar+Screenlet+(Vista'ish+look)?content=63172]("http://www.gnome-look.org/content/show.php/Sidebar+Screenlet+(Vista'ish+look)?content=63172")

---

### Post by esoxLucius4 on 2007-11-05
> **santiagoward2000 said:**
> Travis is right. I haven't seen a sidebar for Gdesklets. But [Screenlets]("www.screenlets.org") have a really cool one!
[http://www.gnome-look.org/content/show.php/Sidebar+Screenlet+(Vista'ish+look)?content=63172]("http://www.gnome-look.org/content/show.php/Sidebar+Screenlet+(Vista'ish+look)?content=63172")

Well, I successfully installed screenlets, but it just stopped working yesterday. Now I can't start them and I can't uninstall them either.

Same happened to awn. I must be natural.

:)

---

### Post by santiagoward2000 on 2007-11-05
> **esoxLucius4 said:**
> Well, I successfully installed screenlets, but it just stopped working yesterday. Now I can't start them and I can't uninstall them either.

Same happened to awn. I must be natural.

:)

Have you tried running them from a terminal, to see if you get any errors?

---

### Post by Andrax on 2007-11-05
How do you install screenlets again? Im kind of a beginner with terminal and stuff so step by step plix!!!

---

### Post by santiagoward2000 on 2007-11-05
> **Andrax said:**
> How do you install screenlets again? Im kind of a beginner with terminal and stuff so step by step plix!!!

Just go to [www.screenlets.org]("www.screenlets.org")
You'll find how to add the repositories for Ubuntu in the faq section.

***_EDIT:_***
:oops: I forgot to mention, to add the repositories, you have to type the following on a terminal:
If you're using Ubuntu: ```
sudo gedit /etc/apt/sources.list
```
If you're using Kubuntu: ```
sudo kate /etc/apt/sources.list
```
If you're using Xubuntu: ```
sudo mousepad /etc/apt/sources.list
```

Then, just go to Synaptic and search for the screenlets package, or open a terminal and type:
```
sudo apt-get install screenlets
```

If you have any problems just yell and I'll try to help (if I'm still awake ;) )

---

### Post by sapatos on 2008-07-15
hi. im newbie how can i download screenlets? thanx

---

