---
title: "wanto execute certain commands every time I boot"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by pompos on 2007-03-05
I want that the following two commands are executed everytime I boot my machine. There can I add them?

echo on > /proc/acpi/fan/FN2/state 
echo 3 > /proc/acpi/fan/FN2/state

---

### Post by JermainWijnhard on 2007-03-05
You can write the code into one of your bashfiles in your home directory. I think i know which one but wont say because im a beginner too and i dont want to give wrong advice. I'm sure a pro will pick this up soon enough :)

---

### Post by konst88 on 2007-03-05
Write it in a script, and add this script to the gnome startup.

---

### Post by Slychilde on 2007-03-05
This may be a little more elegant solution.  I believe it will execute the commands regardless of who logs in, which I assume you'd like.

```
sudo gedit /etc/rc.local
```
and add your commands to the end of the file
```
echo on > /proc/acpi/fan/FN2/state
echo 3 > /proc/acpi/fan/FN2/state
```
I noticed that in Ubuntu it says "In order to enable or disable this script just change the execution bits." in rc.local.  I have no clue what that means; maybe change permissions to make it executable? I know it works 'out of the box' in Arch.
(Disclaimer: I do this in Arch, but I'm pretty sure it'll work in Ubuntu. I added hdparm -a 512 /dev/sda to adjust it's read-ahead for better performance.)

---

### Post by pompos on 2007-03-05
hmm... I found that /etc/rc.local too... however there is one thing I don't really like... It says:

# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.

Is it really just executed on boot up and not some time during the operation time (the time where you can do something with the OS ;); don't now how its called)?

On Gentoo I had somewhere a file called local.start... which worked fine :D

---

### Post by glotz on 2007-03-05
> **pompos said:**
> echo on > /proc/acpi/fan/FN2/state 
echo 3 > /proc/acpi/fan/FN2/state
The latter will overwrite the former! Did you mean >> perhaps?

---

### Post by pompos on 2007-03-05
> **glotz said:**
> The latter will overwrite the former! Did you mean >> perhaps?
no...

echo on > /proc/acpi/fan/FN2/state 
turns off the first fan

echo 3 > /proc/acpi/fan/FN2/state
turns off the second fan

they work perfectly... I am just lazy and don't want to type these commands into the console everytime I boot my laptop...

---

