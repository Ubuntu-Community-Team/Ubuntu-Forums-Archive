---
title: "Problem with installing Arch."
date: 2008-02-15
forum: Arch and derivatives
---

### Post by israelha on 2008-02-15
Hello friends, wussup?

i have a 'little' problem when i am installing Arch from Gui to Virtualbox.

look:
[http://img256.imageshack.us/my.php?image=snapshot3ex2.png](http://img256.imageshack.us/my.php?image=snapshot3ex2.png)

i don't have the option "install kernel".

Some Help please?


BTW, Good morning!

---

### Post by Tenken on 2008-02-15
The kernel is installed along with the packages in Arch. It used to be separate, they might not have update the wiki if that's what you're using.

---

### Post by israelha on 2008-02-15
ok.
but i installed all the steps, step by step,
and i did reset to the machine and anything happen.
only black screen on the background.:confused:

---

### Post by bwtranch on 2008-02-15
> **israelha said:**
> ok.
but i installed all the steps, step by step,
and i did reset to the machine and anything happen.
only black screen on the background.:confused:
Does the screen have an "X" in the middle or is it just blank?

---

### Post by israelha on 2008-02-15
Just Blank!

---

### Post by bwtranch on 2008-02-15
Okay, sounds like the xserver is either not installed or not configured properly. To find out your graphics card OEM, run:
```
 lspci | grep VGA 
```
To look at the xserver file
```
 nano /etc/X11/xorg.conf
```
For general system settings:
```
 nano /etc/rc.conf
```
We may have to backtrack a few steps and see where you are. Follow the guide at [http://wiki.archlinux.org/index.php/Beginners_Guide#.2Fetc.2Frc.conf](http://wiki.archlinux.org/index.php/Beginners_Guide#.2Fetc.2Frc.conf) and make sure you complete each step before moving on.

---

### Post by israelha on 2008-02-15
BTW i didn't change any configuration in the installation.
if it can help..:confused:

---

### Post by bwtranch on 2008-02-15
> **israelha said:**
> BTW i didn't change any configuration in the installation.
if it can help..:confused:
Ah, but you may have needed to:) I need to understand exactly where you are in the build process. If you can reference the above link and tell me where you are, then we can go forward.

---

### Post by Rumor on 2008-02-15
I have no experience installing Arch in a virtual box environment. If all you have done is the install routine from the install ISO, then you have not yet installed xorg or a gui desktop. You need to install those first.

---

### Post by K.Mandla on 2008-02-15
Isn't it triggered after the configure system step?

---

### Post by israelha on 2008-02-15
> **bwtranch said:**
> Ah, but you may have needed to:) I need to understand exactly where you are in the build process. If you can reference the above link and tell me where you are, then we can go forward.

ok i m in 'Configure The System'
i didn't change anything in the installation.
i created Partitions and installed packages,

thanks for helping.

---

### Post by bwtranch on 2008-02-16
Ok, just relax. Let's have the output of ```
 nano /etc/rc.conf
```

---

### Post by israelha on 2008-02-16
here:
[[IMG]http://img341.imageshack.us/img341/841/snapshot4hy0.th.png[/IMG]](http://img341.imageshack.us/my.php?image=snapshot4hy0.png)

[[IMG]http://img156.imageshack.us/img156/7566/snapshot5ce5.th.png[/IMG]](http://img156.imageshack.us/my.php?image=snapshot5ce5.png)

[[IMG]http://img512.imageshack.us/img512/8033/snapshot6uu0.th.png[/IMG]](http://img512.imageshack.us/my.php?image=snapshot6uu0.png)

---

### Post by bwtranch on 2008-02-16
You haven't gotten to the point of installing X. If your host requires dynamic ip addressing, you will need to make the line read eth0="dhcp". If you have to have a static ip, then you will enter it there as well. Keep the subnet the same 255.255.255.0
Make sure you create a root password or you won't be able to log in. Re-boot and you will still be in terminal since we haven't installed X yet. Try to ping google:
```
 ping -c 3 www.google.com/ 
```
If that's successful, then you are online and can continue with "Configuring the System" in the wiki Follow the instructions and use Gnome as a DE (desktop environment). It is easier and works like Ubuntu. Lemme know how it's going. PS I would have got back sooner, but some strorms knocked out the wireless for a while.

---

### Post by bwtranch on 2008-02-16
BTW, when you log in, your user name is root. You'll create regular users later.

---

### Post by israelha on 2008-02-17
> **bwtranch said:**
> You haven't gotten to the point of installing X. If your host requires dynamic ip addressing, you will need to make the line read eth0="dhcp". If you have to have a static ip, then you will enter it there as well. Keep the subnet the same 255.255.255.0
Make sure you create a root password or you won't be able to log in. Re-boot and you will still be in terminal since we haven't installed X yet. Try to ping google:
```
 ping -c 3 www.google.com/ 
```
If that's successful, then you are online and can continue with "Configuring the System" in the wiki Follow the instructions and use Gnome as a DE (desktop environment). It is easier and works like Ubuntu. Lemme know how it's going. PS I would have got back sooner, but some strorms knocked out the wireless for a while.

Hi..
i will check your instructions tommorow,
i have a bug text in history![[[

Thanks for help and be around.:)

---

