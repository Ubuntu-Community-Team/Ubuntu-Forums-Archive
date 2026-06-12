---
title: "Update manager"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by jcats on 2007-11-17
On start up today, the update icon shows. So I open it and it shows 3 updates for Evolution e mail. I am using Thunderbird, so I don't want them. I uncheck them and close out. But the icon will not go away and it always shows the same up dates. What do I have to do to not get these updates and have the update manager not send them in the future?
Thanks;
jcats

---

### Post by OldTimeTech on 2007-11-17
go ahead and let them update....even if you don't use evolution it still has it on your system.  Won't or shouldn't mess with your thunderbird.

---

### Post by jcats on 2007-11-17
Thanks OldTimeTech;
I wasn't so worried about the updates messing with Thunderbird. I'm just thinking, over the long term, I'm going to end up with a lot of updates/programs I don't need or use. I'm trying to figure out a way to not download programs, and have the update manager remember what I have unchecked.
Thanks again;
jcats

---

### Post by SOULRiDER on 2007-11-17
Youc an use aptitude to hold packages so they wont ask for updates.
```
sudo aptitude hold <package-name>
```

If a package asks for an upgrade it means its on your system though, also, you wont end up with unwanted applications simply because new applications wont be installed automatically.

---

### Post by rsambuca on 2007-11-17
You should also be able to use the Synaptic Package Manager.  Select on a package that you have installed, and select "Package" from the top menu.  Click "Lock Version", and it should ignore future updates (I think!).

---

### Post by rsambuca on 2007-11-17
Keep in mind that certain parts of evolution (the calendar, for instance) are used on the Gnome panel.  You might not want to disable security patches for these types of things.

---

### Post by jcats on 2007-11-17
Thank you for the responces.
rsambuca- I tried your idea of going thru the package manager. Apparently, I don't have anything installed from Evolution, because no packages were listed. And when I went thru the differevt menus, "lock" was greyed out.

SOULRiDER-I used your code and it ran ok. But I still have the update manager telling me I have Evolution updates. Maybe I have to install these as there were there before I put in the hold?

Thanks again for all your thoughts.
jcats

---

