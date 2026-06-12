---
title: "how do i change the splash screen"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by slymi2005 on 2007-08-26
how do i change the splash screen, im using xubuntu.

---

### Post by Dark Star on 2007-08-26
There are few thing still left :)

**1**.How to change splash screen that appear after password .... To do install any of the application mentioned below :)

**Install is not present by default :-**

```
sudo apt-get install gnome-splashscreen-manager
```

**Run (Through Alt+F2 or Terminal):**

```
gnome-splashscreen-manager
```

Above will install Splash Screen Manager...

One of th easiest of em.. Is Splash Screen which I am using currently :--

```
sudo apt-get install gnome-art
```

To use it after installing you will find the application under System -> Administration.

Click **Install,** choose the **image file (PNG or JPG)** and it must appear in the window thus. Click **Activate,** re-login to see it in effect.

Now you need to change the background of Ur Splash Screen to match the image... To do this go to System Then point towards Administration and Open Log In Windows.. Under Local Tab u'll find Color option change it accc to ur Splash screen....

**Splash Screen :-** [GNOME-Look.org](http://www.gnome-look.org/index.php?xcontentmode=160)

Note: Splash Screen are different from Boot Screen so make sure u download splash screen which looks like Rectangular Image .. For Example..Here is my current Splash Screen :D

[CENTER][IMG]http://www.imgx.org/files/2672_nay0a/OSX.png[/IMG][/CENTER]

Peas Ds

---

### Post by slymi2005 on 2007-08-26
I followed the steps and got this:

/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_param_spec_boxed: assertion `G_TYPE_IS_BOXED (boxed_type)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_param_spec_boxed: assertion `G_TYPE_IS_BOXED (boxed_type)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed

---

### Post by TeaSwigger on 2007-08-26
Hello,

Because they are different things, I have to ask if you mean the screen where you pick which operating system to boot up (if you're set up to show that screen) or the screen displayed most of the time xubuntu's booting? 

EDIT: Or the screen where you log in? Or the screen after you log in before the desktop comes up? Arrgh! hehe

---

### Post by slymi2005 on 2007-08-26
sorry about being unclear but I am referring to the screen after you log in and it is loading the desktop.

---

### Post by gundumfx on 2007-08-26
> **Dark Star said:**
> There are few thing still left :)

**1**.How to change splash screen that appear after password .... To do install any of the application mentioned below :)

**Install is not present by default :-**

```
sudo apt-get install gnome-splashscreen-manager
```

**Run (Through Alt+F2 or Terminal):**

```
gnome-splashscreen-manager
```

Above will install Splash Screen Manager...

One of th easiest of em.. Is Splash Screen which I am using currently :--

```
sudo apt-get install gnome-art
```

To use it after installing you will find the application under System -> Administration.

Click **Install,** choose the **image file (PNG or JPG)** and it must appear in the window thus. Click **Activate,** re-login to see it in effect.

Now you need to change the background of Ur Splash Screen to match the image... To do this go to System Then point towards Administration and Open Log In Windows.. Under Local Tab u'll find Color option change it accc to ur Splash screen....

**Splash Screen :-** [GNOME-Look.org](http://www.gnome-look.org/index.php?xcontentmode=160)

Note: Splash Screen are different from Boot Screen so make sure u download splash screen which looks like Rectangular Image .. For Example..Here is my current Splash Screen :D

[CENTER][IMG]http://www.imgx.org/files/2672_nay0a/OSX.png[/IMG][/CENTER]

Peas Ds

well thanks

---

### Post by gundumfx on 2007-08-26
> **Dark Star said:**
> There are few thing still left :)

**1**.How to change splash screen that appear after password .... To do install any of the application mentioned below :)

**Install is not present by default :-**

```
sudo apt-get install gnome-splashscreen-manager
```

**Run (Through Alt+F2 or Terminal):**

```
gnome-splashscreen-manager
```


Above will install Splash Screen Manager...

One of th easiest of em.. Is Splash Screen which I am using currently :--

```
sudo apt-get install gnome-art
```

To use it after installing you will find the application under System -> Administration.

Click **Install,** choose the **image file (PNG or JPG)** and it must appear in the window thus. Click **Activate,** re-login to see it in effect.

Now you need to change the background of Ur Splash Screen to match the image... To do this go to System Then point towards Administration and Open Log In Windows.. Under Local Tab u'll find Color option change it accc to ur Splash screen....

**Splash Screen :-** [GNOME-Look.org](http://www.gnome-look.org/index.php?xcontentmode=160)

Note: Splash Screen are different from Boot Screen so make sure u download splash screen which looks like Rectangular Image .. For Example..Here is my current Splash Screen :D

[CENTER][IMG]http://www.imgx.org/files/2672_nay0a/OSX.png[/IMG][/CENTER]

Peas Ds



wel could not download any of the commands it gave me this

 E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


so what

---

### Post by TeaSwigger on 2007-08-26
> **gundumfx said:**
> wel could not download any of the commands it gave me this

 E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


so what

Okay that means that you need to open a terminal window and enter this:

```
sudo dpkg --configure -a
```

before trying to install anything.

---

### Post by TeaSwigger on 2007-08-26
gundumfx, I started xubuntu to find out the splash thing for you. If this works you can skip all those instructions (except my previous post - you need to run that to fix a hiccup in your installer).

Open a terminal and type this:

```
xfce-setting-show splash
```

This should open a handy window where you can easily pick your splash screen, if that's what you're after. :)

---

### Post by slymi2005 on 2007-08-26
okay so i still dont know how to install a splash screen (as the thing you see after you log in and it starts loading things).

---

### Post by gundumfx on 2007-08-26
> **TeaSwigger said:**
> gundumfx, I started xubuntu to find out the splash thing for you. If this works you can skip all those instructions (except my previous post - you need to run that to fix a hiccup in your installer).

Open a terminal and type this:

```
xfce-setting-show splash
```

This should open a handy window where you can easily pick your splash screen, if that's what you're after. :)

thanks for the help

---

