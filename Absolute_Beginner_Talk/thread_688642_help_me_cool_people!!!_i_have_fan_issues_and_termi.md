---
title: "help me cool people!!! i have fan issues and terminal issues and im no good at code!!"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by laurencemulchrone on 2008-02-05
hey people of the linux!

i have an old notebook (compaq presario m700////800mhz; 256mb ram.

the fans never come on and they blaintently need to !!!! the notebook gets soo hot!!

i have read in other places how to force the fans on but i am having trouble. i wrote all the things that they told me to, I.E /etc/modules but wen i type that it says permission deneid or somthing like that...

can someone please help me! how can i get it undenied and how can i force my fans on!! bear in mund i am no good at any of that code stuff and overall i am a confused linuz user.

a million internets to the person whoi helps me out!!!

thanks:)

---

### Post by akiratheoni on 2008-02-05
I'm not too experienced about the fans issue, but if you're having permission issues, use sudo or gksudo. For example, when launching Gedit to edit a file with root access, go to Applications -> Accessories -> Terminal and type:

```
gksu gedit /path/to/file
```

If you'll be using a terminal text editor to edit the text file, use:

```
sudo vi /path/to/file
```

Hope this helps.

---

### Post by MasterXandrex on 2008-02-05
The error about permission denied is simply that you are attempting to edit a system file as a normal user. I would suggest that you open the terminal and use sudo (type "man sudo") if you want a full explanation. Basically it gives you super user ability for only one line without knowing the root password (**_S_**uper **_U_**ser **_DO_**). "gksudo" gives a graphical user interface in which to enter your password.

The only other thing that I would suggest is not using **vi**, as for a new user it can have a bit of a learning curve. I would suggest that instead you use nano, it's a little less feature rich and it's not that good to edit long system files, but if you have trouble with **vi...**

For Nano:
   Crtl+O -- Save
   Crtl+X -- Exit

For vi (Use ':' to enter command mode)
   :wq -- save and quit
   :q -- quit if the file is unedited
   :q! -- force quit (quit without saving)


Xan

---

### Post by laurencemulchrone on 2008-02-05
hey guys thanks for all ur help but everyting u have sed is all above my level !!

i typed in sudo vi /etc/modules and teh terminal took me their but then i tried to use the arrow keeys to go down and add varios words that another thread told me two but nothing worked

i am so confused 

all i want to do is force my fan on!!

:((

---

### Post by timbounceback on 2008-02-05
```
gksudo gedit /etc/modules
```
should do the trick

---

### Post by laurencemulchrone on 2008-02-05
to be honest really i have NO IDEA what i am doing in this terminal thing.

i have no experience with a command line interface...

its all so difficult but im willing to learn:(:)

---

### Post by seventhc on 2008-02-05
the easiest way I can think of for you would be to open a terminal and paste this in:
```
sudo gedit /etc/modules
```

---

### Post by timbounceback on 2008-02-05
have you tried what i suggested?

---

### Post by Nythain on 2008-02-05
you could try nano instead of vi... just replace vi with nano, its another terminal text editor... i find it a bit easier to navigate than vi... figuring out how to save and exit was tricky... control+x exits, when you do that it will ask if you want to save, y for yes, and enter to save as teh filename you opened it up as

---

### Post by akiratheoni on 2008-02-05
Oops, my bad, I put vi instead of nano. Nano's an easier editor than Vi.

---

### Post by MasterXandrex on 2008-02-05
> **Nythain said:**
> you could try nano instead of vi... just replace vi with nano, its another terminal text editor... i find it a bit easier to navigate than vi... figuring out how to save and exit was tricky... control+x exits, when you do that it will ask if you want to save, y for yes, and enter to save as teh filename you opened it up as

Crtl + O saves without exiting... As I stated earlier on this page   :twisted:


Xan

---

### Post by bodhi.zazen on 2008-02-05
> **seventhc said:**
> the easiest way I can think of for you would be to open a terminal and paste this in:
```
sudo gedit /etc/modules
```

Please use gksu with graphical apps, like nautilus and gedit. kdesu with kde (and kate).

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by seventhc on 2008-02-05
> **bodhi.zazen said:**
> Please use gksu with graphical apps, like nautilus and gedit. kdesu with kde (and kate).
Sorry about that,
I'll try. But from all the years of doing '*su*' and now '*sudo*' I tend to forget the other option when in graphical. I think now that you have pointed it out, I will remember better. :D
Is *gksu* the same as *gksudo*? If so I prefer gksu.

---

### Post by bodhi.zazen on 2008-02-05
yea, I think gksu is a sym link to gksudo

---

### Post by laurencemulchrone on 2008-02-08
well thganks people of teh linux!!

afta usin nano insted of vi i maneged it and had epic winz

so all those internets go to whoever suggested nano!!
my noitebook works l33t now so cheers dudes

---

