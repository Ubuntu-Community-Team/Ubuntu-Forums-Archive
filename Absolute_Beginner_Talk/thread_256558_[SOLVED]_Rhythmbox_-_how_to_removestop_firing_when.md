---
title: "[SOLVED] Rhythmbox - how to remove/stop firing when ipod connects"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by chochem on 2006-09-13
... or Rhythmbox - a pain in the pod.

The title really says it: I don't want Rhythmbox to startup just because I connect my ipod. I haven't succeeded in removing it using Synaptic - apparently because it's part and parcel of the ubuntu-desktop element? When I try to remove it along with dependencies, Ubuntu simply quits the process ('apply') and returns me to Synaptic without having removed anything. And the 'preferences' section is a joke - no option to control anything about how the program behaves.

So if anybody can help me either remove it or make it sit quietly at the back, I'd be grateful :)

---

### Post by Jagot on 2006-09-13
Go to System -> Preferences -> Removable Drives and Media.

Now go to the Multimedia tab and at the bottom should be a heading relating to portable music players and what Ubuntu does with them.  By default, as you've found out, Rhythmbox opens up.  Just untick the box and Rhythmbox will now not load when you plug in the iPod.

---

### Post by chochem on 2006-09-13
Thanks Jagot :)

---

### Post by Vegetarianrage on 2008-05-15
This is no longer in option in newer rhythmbox installations. I'm using hardy and i'm having the same initial problem. I like rhythmbox more or less... but this ipod mania is killing me.

---

### Post by mithritades on 2008-05-15
when i go into remove drives an media,there's a pop-up that says the "hald"service is required but not not currently running.
Enable the service and rerun the application,or contact ur system admin.
how do i enable this?

---

### Post by mozetti on 2008-05-15
> **Vegetarianrage said:**
> This is no longer in option in newer rhythmbox installations. I'm using hardy and i'm having the same initial problem. I like rhythmbox more or less... but this ipod mania is killing me.

It's not a Rhythmbox preference, it's an Ubuntu preference. Go to the Ubuntu System Menu, as one of the repliers mentioned above.

---

### Post by nycjeff on 2008-05-16
>It's not a Rhythmbox preference, it's an Ubuntu preference. Go to the Ubuntu System Menu, as one of the repliers mentioned above.<<

I think he's saying that it doesn't appear to be an Ubuntu preference anymore (in Hardy, 8.04), at least not where it used to be.

---

### Post by Vegetarianrage on 2008-05-16
Maybe I just didn't notice where the solution was written so I'll just write what I did.

1. Open filebrowser/nautilus.
2. Click Edit > Preferences.
3. Go to the tab on the far right. There will be an option there for Music 
4. Players, make it so that rockbox is not selected.

5. ?????

6. Profit!

---

### Post by luts on 2008-06-20
> **Vegetarianrage said:**
> Maybe I just didn't notice where the solution was written so I'll just write what I did.

1. Open filebrowser/nautilus.
2. Click Edit > Preferences.
3. Go to the tab on the far right. There will be an option there for Music 
4. Players, make it so that rockbox is not selected.

5. ?????

6. Profit!

10 points to you!

---

### Post by bomanizer on 2008-07-23
There's a tick to disable all programs from starting when inserting media, etc. Thank god, boy that was annoying. Reminded me of Windows a bit too much :D :D

---

