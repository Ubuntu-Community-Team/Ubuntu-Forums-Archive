---
title: "recovery mode"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by STREETURCHINE on 2006-11-21
ok how do i get in to the recovery mode.

---

### Post by taurus on 2006-11-21
Turn your machine on and at the GRUB menu, use the down arrow to highlight the recovery mode and hit Enter...

---

### Post by ewl1217 on 2006-11-21
I just thought I should mention that you may need to hit ESC to see the GRUB menu.

---

### Post by STREETURCHINE on 2006-11-21
yes i thought i may need to hit esc ,nothing happens when i reboot and hit esc it just keeps on loading,is there anouther way to get there

---

### Post by bodhi.zazen on 2006-11-21
In a terminal type:
```
sudo init 1
```

---

### Post by ewl1217 on 2006-11-21
Just watch the messages going by during boot-up. Look closely and have your finger on Esc.

**EDIT:**> ```
sudo init 1
``` That's it? I've never seen that before...

---

### Post by STREETURCHINE on 2006-11-21
> **ewl1217 said:**
> Just watch the messages going by during boot-up. Look closely and have your finger on Esc.

**EDIT:** That's it? I've never seen that before...

yes i have done that but it refuses to go to recovery it just keeps on booting,i have done about 40 reboots and it wont behave:D

---

### Post by bodhi.zazen on 2006-11-21
> **ewl1217 said:**
> Just watch the messages going by during boot-up. Look closely and have your finger on Esc.

**EDIT:** That's it? I've never seen that before...

To change back:

```
init 2
```

8)

---

### Post by STREETURCHINE on 2006-11-21
> **bodhi.zazen said:**
> In a terminal type:
```
sudo init 1
```

ok i have typed that in,here is the result

* init: going single user
* init: sending processes the term signal
* init: sending processes the kill signal
root@linux~#

ok so now what do i do now ,

---

### Post by taurus on 2006-11-21
Did you modify your /boot/grub/menu.lst at all?  Boot your machine with the LiveCD, mount the partition where /boot is (if you don't have separate /boot, then mount /), and paste your /boot/grub/menu.ls here then...

---

### Post by STREETURCHINE on 2006-11-21
> **taurus said:**
> Did you modify your /boot/grub/menu.lst at all?  Boot your machine with the LiveCD, mount the partition where /boot is (if you don't have separate /boot, then mount /), and paste your /boot/grub/menu.ls here then...

thanks taurus ,i dont think i did anything to the grub menu.i installed beryl and everything went south,i can still load ubuntu ok ,it is just that my window's get stuck up in the top left hand corner and i cant move them,
the only way i can close them is by going file/exit,there is no icons on them to shut themdown or to minamise them.
so i thought recovery was the way to go.
ps..i uninstalled beryl but the problem remained,

i

---

### Post by bodhi.zazen on 2006-11-21
> **STREETURCHINE said:**
> ok i have typed that in,here is the result

* init: going single user
* init: sending processes the term signal
* init: sending processes the kill signal
root@linux~#

ok so now what do i do now ,

I do not know. You are in recovery mode as you requested.

Type:```
nano /boot/grub/menu.lst
```To edit your grub menu.

Type```
init 2
```to return to your gui. It may be easier to post menu.lst from your GUI.

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by STREETURCHINE on 2006-11-21
i am on my laptop here with windows ,it seems my boot menu list is empty

no sorry typo when i enterd the command,but i cant paste as i have to close each window so i can open the next

---

### Post by taurus on 2006-11-21
> **STREETURCHINE said:**
> i am on my laptop here with windows ,it seems my boot menu list is empty
It can't be empty or you won't be able to boot Ubuntu!!!  Are you sure you look in /boot/grub/menu.lst?

---

### Post by STREETURCHINE on 2006-11-21
yep sorry people it has stuff in it ,typo when entering the command.

sorry i cant paste anything so you can help me may just have to bite the bullit and reinstall,](*,)

---

### Post by taurus on 2006-11-21
Why reinstall when it's so easy to fix.  

1.  Make sure you set the "timeout" to 10 (for 10 seconds delay)...
2.  Make sure the line with "hidemenu" is command out...
```
#hiddenmenu
```
3.  Make sure you have an entry for "(recovery mode)" (usually the second entry after the acutally kernel)...

---

### Post by STREETURCHINE on 2006-11-21
> **taurus said:**
> Why reinstall when it's so easy to fix.  

1.  Make sure you set the "timeout" to 10 (for 10 seconds delay)...
2.  Make sure the line with "hidemenu" is command out...
```
#hiddenmenu
```
3.  Make sure you have an entry for "(recovery mode)" (usually the second entry after the acutally kernel)...

hidemenu is commented out,timeout set to 10 sec,
and there is a recovery mode in there,
i dont know if this has anything to do wiyh it but i get an error message in terminal,
gnomeUI warning while connecting to session manager authentication rejected .none of the authentication protocols specifiedare supported and host based authentication failed

---

### Post by STREETURCHINE on 2006-11-21
s is a screenshot of what is happening,as you can see there is no bar above the (file.edit.view.go bookmarks.tools.help) [ATTACH]19772[/ATTACH]

---

