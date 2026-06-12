---
title: "Still Stuck Invest Aplet"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by mgaskell on 2007-01-21
Hi,

Still can't get the darn invest aplet off the upper panel. It doesn't work. Cannot configure it, cannot open it, cannot delete it from the panel.

Edgy newby.

](*,) 

Thanks

---

### Post by jordanmthomas on 2007-01-22
I just read your post and wondered what could be so hard about it.  But, rather than telling you to remove it the normal way I decided to have a try at it myself.  

I now understand your problem.  Here is how I (finally) got rid of it.
Press Alt+F2 and type
```
gconf-editor /apps/panel/applets
```
On the left there are some folders labeled applet_x
find the one with the bonobo_iid of Invest_Applet.  In my screenshot, I have found the deskbar applet, highlighted in red
[img]http://img258.imageshack.us/img258/9319/screenshot21fb.png[/img]

Keep the number in mind (in my example, we will use 5)

Open a terminal up and type this:
```
cd ~/.gconf/apps/panel/applets
```
Now, remove the directory of applet_5 (or whatever your number is)
```
rm -r applet_5 # remember to change 5 to the right number!
```
Now, back in your gconf window, click on the general folder on the left (so you will be in /apps/panel/general)
and then double click on applet_id_list in the right pane like I have done in this screenshot:
[img]http://img109.imageshack.us/img109/5131/screenshot32ht.png[/img]
Now, find applet_5 (or whatever yours is) and click on it.  Then, click on remove.

Yay, it is gone now!  You can either log out and then back in or press Alt+F2 and then type 
```
killall gnome-panel
``` and your panel will restart, sans invest applet


P.S.  That sure was a pain to get rid of, what's the deal with that?

**edit**  I actually was able to remove it by right clicking just to the right of it and going to remove...it was just kind of hard to find it exactly

---

### Post by emperor on 2007-09-12
> **mgaskell said:**
> Hi,
Still can't get the darn invest aplet off the upper panel. It doesn't work. Cannot configure it, cannot open it, cannot delete it from the panel.
Edgy newby.
  Thanks

See bug report:
[https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/59060](https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/59060)

Open a terminal and get "pid #":

$ ps ax | grep invest

Then:
kill -9 "pid #r"

Finally, answer no to reload.

---

### Post by adrien214 on 2007-10-21
what if I actually want to use the applet ? killing or removing the applet doesn't solve the problem

:confused:

the easiest solution is :

"I've discovered that what appears to be unused grey space to the right of the applet is probably intentional. If you right click on the grey space you will see the options for removal.
..."

found at [https://bugs.launchpad.net/gnome-applets/+bug/59060](https://bugs.launchpad.net/gnome-applets/+bug/59060)

---

