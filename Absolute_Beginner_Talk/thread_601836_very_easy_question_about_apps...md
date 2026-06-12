---
title: "very easy question about apps.."
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by jake16424 on 2007-11-03
how do i find which ones are installed on this linux machine besides the damned packagmanager and searching for the name of the package i had allready installed?

---

### Post by bluepowder7 on 2007-11-03
when you open Synaptic, on the bottom left there's a bunch of buttons.  click STATUS, then select INSTALLED.  that should show you what you want to see.

---

### Post by jake16424 on 2007-11-03
> **bluepowder7 said:**
> when you open Synaptic, on the bottom left there's a bunch of buttons.  click STATUS, then select INSTALLED.  that should show you what you want to see.

i've been looking for something like this sense last night, haha.. wow talk about in plain sight, thank you very much.. =D  :KS

---

### Post by FranMichaels on 2007-11-03
You can use the Synaptic Package Manager without searching one by one, click the button at the lower left *Status*
Then choose (from the left column) *Installed*.

That will show a nice list.

If you meant you want a full list, without using GUI, you can do so from Terminal

```
dpkg --get-selections
```

If you'd like it in a text file for example

```
dpkg --get-selections > installed.txt
```

Hope this helps you. :)

---

### Post by bluepowder7 on 2007-11-03
> **jake16424 said:**
> i've been looking for something like this sense last night, haha.. wow talk about in plain sight, thank you very much.. =D  :KS

no problem!  up until you asked, i didn't actually know if anything was there, but figured i'd check just in case there's some menu command or something.  until a few days ago, i didn't even know that Synaptic existed or what it was for.

---

### Post by Maestro23 on 2007-11-03
> **jake16424 said:**
> i've been looking for something like this sense last night, haha.. wow talk about in plain sight, thank you very much.. =D  :KS

All about Synaptic: [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by mali2297 on 2007-11-03
If you've got a section open in Synaptic with a long list of packages, you can click on the header of the leftmost column to sort the entries according to status. That way you can get all the installed packages to be listed first for that particular category.

---

### Post by jake16424 on 2007-11-03
yeah thank you guy's for the help, now i can see what's installed and what's not installed,

but there is one thing that is confusing.

i have installed a game, Atanks or somthing like that.

but under teh game drop down list it isn't listed, any ideas?

---

### Post by Dr Small on 2007-11-03
Press ALT+F2 (Run dialog) and type in the name of the app you installed, or run it from the terminal.

Dr Small

---

### Post by jake16424 on 2007-11-03
> **Dr Small said:**
> Press ALT+F2 (Run dialog) and type in the name of the app you installed, or run it from the terminal.

Dr Small


how would one do the running from the terminal?

---

### Post by Maestro23 on 2007-11-03
> **jake16424 said:**
> how would one do the running from the terminal?

Open a terminal and type the name of the program.

---

### Post by mali2297 on 2007-11-03
My guess is that the command is
```

atanks

```

If that doesn't work, try
```

apropos tanks

```
Then you should get a list of commands that are associated with the keyword "tanks".

EDIT:
Also note that Linux is case-sensitive, i.e. it doesn't read "Atanks" and "atanks" as the same word.

---

### Post by jake16424 on 2007-11-03
> **Maestro23 said:**
> Open a terminal and type the name of the program.

name of program, as of synaptic package manager.

= atanks

i type atanks into the terminal, an it says

wow, never mind cause it just decided to work,, that is oddd.. lol

ive tried this 3times, to no avail, haha.. =-D

---

