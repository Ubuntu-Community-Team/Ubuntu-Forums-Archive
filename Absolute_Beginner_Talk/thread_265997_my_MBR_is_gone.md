---
title: "my MBR is gone ?"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by porsher_puddles on 2006-09-26
I was running dapper drake and win xp, it took me ages to download all the updates for dapper as i'm on dial up but finally everything was working fine, until windows got a virus which stuffed up my connection to the internet, as i no longer had the option to use dial up after i got rid of the virus, so i had to reinstall.
Now my mbr is overwritten by windows, How do i fix it so ubuntu is back, i have read through a few threads but they seem to be written for hoary and it seems slightly diffrent, can someone please tell me a simple way to fix this as i'm  having trouble,especially as i don't fully understand the patitioner and don't want to have to start from scratch

---

### Post by bulldog on 2006-09-26
Boot the live cd and do the following steps takes 5 minutes to do.

When you get to the desktop open a terminal and enter. 

```
 sudo grub 
```


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands



```
find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


```
setup (hd0)
```


Finally exit the grub shell

```
quit
```

---

### Post by whizbaby on 2006-09-26
Her a link for those who like to install the dozer over and over and get the grub back quickly:
[http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

---

### Post by gn2 on 2006-09-26
> **porsher_puddles said:**
> I was running dapper drake and win xp, it took me ages to download all the updates for dapper as i'm on dial up but finally everything was working fine, until windows got a virus which stuffed up my connection to the internet, as i no longer had the option to use dial up after i got rid of the virus, so i had to reinstall.
Now my mbr is overwritten by windows, How do i fix it so ubuntu is back, i have read through a few threads but they seem to be written for hoary and it seems slightly diffrent, can someone please tell me a simple way to fix this as i'm  having trouble,especially as i don't fully understand the patitioner and don't want to have to start from scratch

This is another reason for F8 dual-booting on separate drives methinks.....

---

### Post by xpod on 2006-09-26
> This is another reason for F8 dual-booting on separate drives methinks..

Your a great fan of that way me scottish pal eh:D 
I think i might be doing it that way if i ever do put xp back on...

If?:D

---

### Post by gn2 on 2006-09-26
Yep definitely an F8 evangelist.

Prevents cross contamination.

---

