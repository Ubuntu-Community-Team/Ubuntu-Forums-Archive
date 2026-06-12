---
title: "How do i compile a theme?"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by Snare on 2006-04-23
I went into system>themes and tried to installd a theme, but it says it needs to be compiled first. can someone point me in the right directions, and maybe show me some good how guides for VERY basic linux things. 

thx

---

### Post by unbuntu on 2006-04-23
Haven't tried myself, but the tar.gz file should contain a README file, in which you can find instruction.

Normally it's a ./configure & make thing...

---

### Post by Snare on 2006-04-23
ok i really am completely new at this...

but it says ./configure but everytime i type that in it tells me its not a valid folder or somethin like that? i extracted the file to a folder on my desktop if that helps at all

it says to 

./configure

make 

then 
make install

but i have no idea what that means to do

---

### Post by unbuntu on 2006-04-23
[QUOTE=Snare]ok i really am completely new at this...

but it says ./configure but everytime i type that in it tells me its not a valid folder or somethin like that? i extracted the file to a folder on my desktop if that helps at all

it says to 

./configure

make 

then 
make install

but i have no idea what that means to do[/QUOTE]

if you untar to the desktop, then you start a terminal, and cd to your desktop folder:

```

cd ~/Desktop

```

and then cd to the folder you extracted to, say abc (under Desktop folder)
```

cd abc

```

then do the rest, namely
```

./configure & make

```
```

sudo make install

```

---

### Post by Snare on 2006-04-23
ok i did the 

```

./configure & make

```

and it goes thru a bunch of stuff and towards the end it says 

```

checking for x...configure: error: Can't find X includes. Please check your installation and add the correct paths!

```

any ides?

and could you explain what the cd thing means? is that telling it to look on the desktop?

---

### Post by unbuntu on 2006-04-23
cd means **c**hange **d**irectory.  Your desktop is the directory called Desktop under your home directory.  Your home directory is a directory under /home/*your_account*

It seems like you don't have the include files.  Try:
```

sudo apt-get install build-essentials

```

---

### Post by croak77 on 2006-04-23
You are gonna need some development headers too. Like libx11-dev and x11proto-core-dev.

---

### Post by Snare on 2006-04-23
ok i tried install those to dev headers, says they were up to date.

in the installer note for the theme is say si need the QT and KDE development header, so i searched for those i found the qt one and i found kde-devel listed as a package, but when i type it in terminal it dosen't find it. and i tried 

sudo apt-get install build-essentials and it says it couldn't be found.

any other ideas?

---

### Post by unbuntu on 2006-04-23
[QUOTE=Snare]
sudo apt-get install build-essentials and it says it couldn't be found.

any other ideas?[/QUOTE]

Sorry the name may not be exactly that, but I'm not on Linux right now, so I can't help with the exact name.  But it's something like that.  Run synaptic to find the packages.
```

sudo synaptic

```
Also you can find those kde qt packages in synaptic

---

### Post by Snare on 2006-04-23
ok, i got the ./configure to work

but when i go back into system>preferences>themese it dosen't show up on the list, but i do have the option to install a theme, but i dont know where to look, or what to look for to get the theme i just configured to show up

oh and i did the

```

sudo make install

``` 

after the ./configure when it said to

---

### Post by croak77 on 2006-04-23
Are you using gnome or kde?

---

### Post by ComplexNumber on 2006-04-23
[quote=croak77]Are you using gnome or kde?[/quote] he seems to be theming kde whilst in gnome :-k

**snare**
you will fine the theme listed in the kde control centre (go to the commandline and type'kcontrol'). you seem to looking for the kde theme in the list of gnome themes. also, what is the name of the theme that you are compiling?

---

### Post by familyjules74123 on 2006-11-06
> **unbuntu said:**
> if you untar to the desktop, then you start a terminal, and cd to your desktop folder:

```

cd ~/Desktop

```

and then cd to the folder you extracted to, say abc (under Desktop folder)
```

cd abc

```

then do the rest, namely
```

./configure & make

```
```

sudo make install

```

I am new to this as well and I have done the steps mentioned above.  Now do I just load it in the theme preferences section?

---

