---
title: "Change Shift+6 key [ ^ ] to Peso symbol [ &#8369; ]"
date: 2012-07-09
forum: Any Other OS
---

### Post by palawanbeach on 2012-07-09
Hello,

How can I turn the Shift+6 key [ **[SIZE="3"][COLOR="red"]^[/COLOR][/SIZE]** ] into the Peso symbol [ **[COLOR="red"][SIZE="4"]&#8369;[/SIZE][/COLOR]** ]?

I am currently travelling and I use the [COLOR="Red"]&#8369;[/COLOR] character much more often than the **[COLOR="red"]^[/COLOR]** character.

---

### Post by palawanbeach on 2012-07-10
xev gives the following printout for **^**


> KeyRelease event, serial 33, synthetic NO, window 0x3e00001,
    root 0xac, subw 0x0, time 1028079, (81,81), root:(87,129),
    state 0x11, keycode 15 (keysym **0x5e**, asciicircum), same_screen YES,
    XLookupString gives 1 bytes: (5e) "^"
    XFilterEvent returns: False


---

### Post by palawanbeach on 2012-07-12
bump

---

### Post by Krytarik on 2012-07-13
Since we are going to remap the key with the keycode 15 (following your 'xev' output), we need to know exactly how it is mapped currently, to retain the other options - so please post the output of:
```
xmodmap -pke | grep " 15 "
```
Regards.

---

### Post by palawanbeach on 2012-07-13
krytarik,
thanks for your post.


>  $ xmodmap -pke | grep " 15 "
keycode  15 = 6 asciicircum 6 asciicircum dead_circumflex dead_circumflex dead_circumflex


---

### Post by Krytarik on 2012-07-13
Thanks for replying that fast - wow! :D

Ok then, create a file called ".Xmodmap" (hidden) in the top-level of your home directory with this content:

~/.Xmodmap:
```
keycode 15 = 6 U20B1 6 U20B1 dead_circumflex dead_circumflex dead_circumflex
```The next time you log in, you may be asked if you want to use that keymap file.* If so, just choose "Add" and confirm with "OK". It should work then.

* depends on what Ubuntu version you are using, and if you already had such a file before, and have already confirmed/disabled that query

---

### Post by palawanbeach on 2012-07-13
Krytarik,
I created a file called .Xmodmap in my Home directory. I logged out and logged in and my Shift-F6 still acts the same way.

---

### Post by Krytarik on 2012-07-13
> **palawanbeach said:**
> I created a file called .Xmodmap in my Home directory. I logged out and logged in and my **Shift-F6** still acts the same way.
You mean Shift + **6**, right?
> **Krytarik said:**
> depends on **what Ubuntu version you are using [?]** ...
... and what desktop environment are you using, i.e. how is the session named you log in to?

---

### Post by palawanbeach on 2012-07-13
Yes, I meant Shift-6. 
I believe I'm using Gnome, but to be sure, how can I double-check?

---

### Post by Krytarik on 2012-07-13
> **palawanbeach said:**
> I believe I'm using Gnome, but to be sure, how can I double-check?
Please post the output of these commands:
```
lsb_release -a
echo $DESKTOP_SESSION
```

---

### Post by palawanbeach on 2012-07-13
Here is the result.
>  lsb_release -a
No LSB modules are available.
Distributor ID:	LinuxMint
Description:	Linux Mint 13 Maya
Release:	13
Codename:	maya

---

### Post by Krytarik on 2012-07-13
> **palawanbeach said:**
> Here is the result.
```
lsb_release -a
No LSB modules are available.
Distributor ID:    LinuxMint
Description:    Linux Mint 13 Maya
Release:    13
Codename:    maya
```
How about the other one?:
> **Krytarik said:**
> Please post the output of these commands:
```
lsb_release -a
**echo $DESKTOP_SESSION**
```

---

### Post by palawanbeach on 2012-07-13
krytarik,

sorry, i overlooked that 2nd command.

here it is.
>  echo $DESKTOP_SESSION
default


---

### Post by Krytarik on 2012-07-13
> **palawanbeach said:**
> ```
lsb_release -a
No LSB modules are available.
Distributor ID: LinuxMint
Description: **Linux Mint 13 Maya**
Release: 13
Codename: maya
```
> **palawanbeach said:**
> ```
echo $DESKTOP_SESSION
**default**
```
Hmm, the 'default' session of Linux Mint 13 Maya according to its [website]("http://www.linuxmint.com/rel_maya_whatsnew.php") is either MATE or Cinnamon, and I have no idea how these are handling Xmodmap files.

Another way to achieve basically the same, however, is to run this command via their respective equivalents of Startup Applications:
```
xmodmap -e "keycode 15 = 6 U20B1 6 U20B1 dead_circumflex dead_circumflex dead_circumflex"
```You may need to add a delay to that command, depending on when the default keymap is loaded. If so, modify the command like this, and set the number after "sleep" to a sufficient number of seconds:
```
sh -c "**sleep 10**; xmodmap -e 'keycode 15 = 6 U20B1 6 U20B1 dead_circumflex dead_circumflex dead_circumflex'"
```

---

### Post by coffeecat on 2012-07-13
> lsb_release -a
No LSB modules are available.
Distributor ID: LinuxMint
Description: Linux Mint 13 Maya
Release: 13
Codename: maya 

*Thread moved to **Other OS/Distro Talk**.*

---

### Post by palawanbeach on 2012-07-13
> **Krytarik said:**
> 
Another way to achieve basically the same, however, is to run this command via their respective equivalents of Startup Applications:
```
xmodmap -e "keycode 15 = 6 U20B1 6 U20B1 dead_circumflex dead_circumflex dead_circumflex"
```You may need to add a delay to that command, depending on when the default keymap is loaded. If so, modify the command like this, and set the number after "sleep" to a sufficient number of seconds:
```
sh -c "**sleep 10**; xmodmap -e 'keycode 15 = 6 U20B1 6 U20B1 dead_circumflex dead_circumflex dead_circumflex'"
```

Thanks Krytarik, I ran the terminal command and it works. I found the app in charge of "Startup Applications" and added the command there. Thank you for all your help. I'm going to transfer back to Ubuntu soon.

---

