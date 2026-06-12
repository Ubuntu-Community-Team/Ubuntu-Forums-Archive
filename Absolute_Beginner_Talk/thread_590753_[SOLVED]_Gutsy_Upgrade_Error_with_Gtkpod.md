---
title: "[SOLVED] Gutsy Upgrade Error with Gtkpod"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by ShadowMKII on 2007-10-25
I have not been able to find this anywhere, and I think it would best be explained through pictures. My Synaptic will not reload properly and I cannot upgrade to Gutsy because of this one bloody issue. Could someone please help me out here?

Here are some links for information's sake:

[[img=http://img206.imageshack.us/img206/8154/screenshottp9.th.png]](http://img206.imageshack.us/my.php?image=screenshottp9.png)
[[img=http://img206.imageshack.us/img206/8261/screenshot1gt5.th.png]](http://img206.imageshack.us/my.php?image=screenshot1gt5.png)
[[img=http://img206.imageshack.us/img206/9060/screenshot2wg8.th.png]](http://img206.imageshack.us/my.php?image=screenshot2wg8.png)
[[img=http://img177.imageshack.us/img177/9127/screenshot3dh1.th.png]](http://img177.imageshack.us/my.php?image=screenshot3dh1.png)
[[img=http://img177.imageshack.us/img177/5116/screenshot4di4.th.png]](http://img177.imageshack.us/my.php?image=screenshot4di4.png)
[[img=http://img520.imageshack.us/img520/6472/screenshot5ow3.th.png]](http://img520.imageshack.us/my.php?image=screenshot5ow3.png)

This may seem like an overload of links, but they are just simple pictures of roughly the same information and are supposed to be a source of reference so that you know exactly what is going on with my Ubuntu while I am trying to update, just to avoid any misinformation or discrepancies in scenarios.

Thank you for your consideration.

---

### Post by RomeReactor on 2007-10-25
Hi. Do you have any extra (non-official) repositories enabled? if you do, you may want to disable them while the upgrade takes place, and later add the proper version of those extra repositories for Gutsy.

If you don't have any extra repositories, try switching to the main repository: in Synaptic, go to "Settings->Repositories", in the first tab (Ubuntu Software) press the drop-down **Download from:** menu, and select "Main". Or select "Other", and press "Select Best Server"; Synaptic will test the servers to find the most adequate one for you.

After choosing the server, if you aren't prompted to do so, press the blue "Reload" button. Now close Synaptic, open Update Manager, and see if you can upgrade now.

As a last resort, you could uninstall gtkpod, do the upgrade, and install it again later.

And as always, remember to back up any important data you may have before trying the upgrade. Have you downloaded an image of Gutsy (Live or Alternate) yet?

---

### Post by ShadowMKII on 2007-10-25
I have not downloaded any images yet. I did not think that I needed to! As for gktpod, I believed that I have got the problem solved. I went to the tab labeled "Third-Party Software" and disabled the whole gtkpod link there. I reloaded and then began to upgrade again. Luckily for me, I recieved no error message... but I do not have enough disk space, which is being discussed on another thread. Thank you for your help! You helped get that big headache out of my way! ^-^

---

