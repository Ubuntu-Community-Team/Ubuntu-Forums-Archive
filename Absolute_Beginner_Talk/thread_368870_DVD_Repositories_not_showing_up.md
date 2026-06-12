---
title: "DVD Repositories not showing up"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by adadof6 on 2007-02-23
Here's a weird one.

Someone gave me 4 DVDs that contain the whole set of i386 repositories. Cool.

I'm running Dapper Drake 6.06.1 and these repositories are for that.

I've added each DVD in Synaptic Package Manager. (Settings > Repositores > Add Cdrom).

It reads each DVD and asks for a title. Fine.

But they don't show up. I click "Reload" and they're not there. Also few of the packages appear in the list of available programs.

For example: I know that "SuperTux" is on one of the DVDs. But it doesn't show up after a search.

Is there some setting somewhere I need to tweak?

---

### Post by taurus on 2007-02-23
What does your /etc/apt/sources.list look like then?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by adadof6 on 2007-02-23
deb cdrom:[Repository DVD #1]/ dapper-updates main multiverse restricted universe
deb cdrom:[Repository DVD #2]/ dapper-updates main multiverse restricted universe
deb cdrom:[Repository DVD #3]/ dapper-updates main multiverse restricted universe
deb cdrom:[Repository DVD #4]/ dapper-updates main multiverse restricted universe

---

### Post by taurus on 2007-02-23
And did you remember to run

```
sudo aptitude update
```

---

### Post by adadof6 on 2007-02-23
Mm.

You may be on the right trail, **taurus**.

I clicked the Update button in Synaptic... but to no avail.

HOWEVER... [dramatic music here] ... I've run that command and here's the output:

```
Err cdrom://Repository DVD #1 dapper-updates/main Packages
Please use apt-cdrom to make this CD-ROM recognized by APT.
apt-get update can not be used to add new CD-ROMs
```

I've never seen this before. Apt-CDROM? Very interesting. Giving it a whirl now . . .

---

### Post by adadof6 on 2007-02-23
That did it.

:popcorn:

Here's the command that solved the problem: ```
sudo apt-cdrom add
```

Kewl.

Sorry it took so long to answer. Here's the reason it did.

The DVDs were already added as available repositories in **Synaptic Package Manager** creating a conflict with **apt**. (**sudo apt-cdrom add** worked but when I called up Synaptic and clicked "reload" it complained of conflicts. *sigh*)

It was necessary to remove all traces of the DVDs from both sources.

[LIST]
[*]/var/lib/apt/cdroms.list was saved as a blank file.
[*]/var/lib/apt/lists - all files removed except the **lock** file and the **partial** folder (and its contents).
[*]/etc/apt/sources.list saved as a blank file.
[/LIST]

At this point **sudo apt-cdrom add** worked perfectly allowing the addition and naming of each DVD. Synaptic Package Manager now displays TONS of available packages.

**NOTE:** For the curious -- **do not try this at home**. These steps are for trained professionals... or really daring people. This was necessary as Synaptic does **not** appear to add DVDs in Dapper Drake properly. Mileage may vary with Edgy Eft and Fiesty Fawn. Breezy Badger's version of Synaptic Package Manager works as it should.

Thanks.

---

