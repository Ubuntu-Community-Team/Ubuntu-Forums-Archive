---
title: "Anyone have any tips to make xubuntu/ubuntu faster?"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by ajskhan on 2007-07-01
Hi 
i have an old laptop and it crashes frequently using FF.

I was wondering if there are any tips to make it faster?

i know i have a really really old and slow pc, but if there are just a few optimization,  i dont mind giving up the looks of linux, as long as it dont crash no more

btw, is there a less resource using browser i could use?

---

### Post by Seisen on 2007-07-01
You can use dillo buts it a pretty basic browser. You can also follow the guides on the link and see if they help any.

[http://ubuntuforums.org/showthread.php?t=189192]("http://ubuntuforums.org/showthread.php?t=189192")

---

### Post by kerry_s on 2007-07-01
yep, switch to fluxbox or icewm or just anything lighter than a full desktop.

[B]sudo apt-get install fluxbox
sudo update-menus
logout and select fluxbox in the session menu
[/B]
i use fluxbox on a 450mhz 256ram.

move firefox's cache to /tmp
about:config
new string

```
**browser.cache.disk.parent_directory**    
**/tmp/firefox**
```

try not to use to many extensions.

for a less resource browser try links2(**sudo apt-get install links2**) launch it with 
**xlinks2 google.com**

it renders better than dillo, but is not as simple.


You should consider doing a custom build with only what you need.
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by kerry_s on 2007-07-01
Oh, i forgot 1 make sure you do the swappiness trick you want to stay as much in ram  as you can.

**gksu mousepad /etc/sysctl.conf**

put

vm.swappiness=0

at the bottom(need to reboot after)

---

### Post by raul_ on 2007-07-01
Use lighter apps, GTK based, and ditch Firefox. I would say kazehakase but the Feisty version is borked. Try Galeon or Opera. For mail try Sylpheed Claws. Dump any application that has a "k" in it :P

---

### Post by ajskhan on 2007-07-01
wait, is fluxbox a different os like xubuntu, ubuntu, etc?

---

### Post by Adam_GUI on 2007-07-01
> **ajskhan said:**
> wait, is fluxbox a different os like xubuntu, ubuntu, etc?

No, fluxbox is a window manager.
If you want to try out a live CD using fluxbox, check out fluxbuntu or Damn Small Linux.

---

### Post by ajskhan on 2007-07-02
hmmm, seems nice, will it make me put in the installation cd (for xubutu?)

window manager? wat on earth is that?
 basically what i am asking is will it allow me to:
check my email using web browser, meebo, download updates, etc without crashing as much?

and is it easy to uninstal?

edit: will it run faster?
and is it easy to use?

---

### Post by kerry_s on 2007-07-02
> **ajskhan said:**
> hmmm, seems nice, will it make me put in the installation cd (for xubutu?)

window manager? wat on earth is that?
 basically what i am asking is will it allow me to:
check my email using web browser, meebo, download updates, etc without crashing as much?

and is it easy to uninstal?

edit: will it run faster?
and is it easy to use?

a WM is the environment displays the apps. you can run it with your existing setup. you will have all your apps in a lighter surrounding. see my post above. it will help speed wise. it takes getting use to, but it's simple. for real speed you would install a fluxbox only system. but sounds like you need to just use linux more till you get use to it so just add it to your current system, you will be using the same apps you have in gnome.

pic of my install->

---

### Post by dptxp on 2007-07-02
Try Puppy Linux.
Last was version 2.16, I think just 100MB download.
Works from RAM, blazing fast.

---

### Post by ajskhan on 2007-07-02
hmmmm, flux seems nice!

but how did you get that bar on the side to pop up?

---

### Post by eternalsword on 2007-07-02
he's probably running conky which doesn't pop up but resides either in it's own window or on the destop.

---

### Post by exploder on 2007-07-02
This should help.

[http://www.xsol.se/?p=26](http://www.xsol.se/?p=26)

---

### Post by ajskhan on 2007-07-02
ok
it just crashed just like regular ubuntu/xubuntu would... do i need to right click the desktop and click windowmanager>>>fluxbox? or do i just use it normally?

---

### Post by eternalsword on 2007-07-02
what do you mean by crashed?  if you can right-click on the desktop it means fluxbox is running already.

by this I mean, did X crash, some Firefox crash, something else crash?

---

### Post by ajskhan on 2007-07-02
i do believe my whole computer crashed

as firefox was still
my cursor wouldn't move, and there was no disk activity

---

### Post by eternalsword on 2007-07-02
okay, you typically need to do a hard reboot in that case.  it's a sign that the kernel crashed.  in that situation if ctrl+alt+f1 doesn't take you to a tty login, then you need a hard reboot.  If it does go to a tty login, then login with your credentials and then type ```
sudo shutdown -r now
``` for a better way to restart.  usually when the kernel crashes like that, it is a sign that some hardware is not setup properly ie incorrect drivers.  You could search the forums for your different hardware specs and see if anyone else has had any issues.

I remember the culprit for me when I had that same issue was the driver for my wireless device.  I ended up using ndiswrapper and disabling the native drivers altogether.

---

