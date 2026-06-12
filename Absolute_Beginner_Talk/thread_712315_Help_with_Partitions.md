---
title: "Help with Partitions"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by wiesjak on 2008-03-01
Im trying to make a partition so i can dual boot between vista and 7.10.

when ever i do the installation on the live cd and try to seperate my new partition it never works can any one help me out. Thanks

---

### Post by wolfen69 on 2008-03-01
can you be more specific about your problem?

---

### Post by wiesjak on 2008-03-01
ok i get to the part in the instalation where you can resize ur HD so i do so and get this dialog box that says 

"Before you can select a new partition size, any previous changes have to be written to disk.

You cannot undo this operation.

Please note that the resize operation may take a long time."

i click continue

then it starts the  after about 2 seconds i get another error box that says:

"An error occurred while writing the changes to the storage devices.

The resize operation is aborted"

then i go to a wierd menu that i dont know what to do

EDIT: Its the same menu you go to if you partition it manually

---

### Post by bren on 2008-03-01
i have heard from several others that it works better to use VISTA itself to

1) reduce the size of the current VISTA partition
2) then start Ubuntu install but choose the manual option for parition
3) choose the empty space to install into

the size you choose for your partitions will be dependent on the space you have.     You could look at how much space your Vista currently uses and add 10 or 20GB extra as margin for the future.    Then convert the rest to free space for Ubuntu

Of course, maybe you don't have the space for that..... The minimum that I have heard people recommending for free space needed for Ubuntu is perhaps 10GB

If you are up for it then search on the web for Hermanzone and Ubuntu install and you will find very detailed advice.

One option that is worth following if you can be bothered are to create separate / (root) /home (home) and data partitions..... this will be a little more work and you can either do it now or later.    The advantage of this approach is that you can reinstall a different version of linux on top of your old install without losing all your config files and programs you installed (much better than windows!)

Anyway ignore that last part for now but consider it for later.

Bren

---

### Post by wiesjak on 2008-03-01
okdo you know how i would make the free space? do i just make sure i have 20 gb free?

---

### Post by bren on 2008-03-02
hi wiesjak

there is (i believe) some kind of partition editor that is supplied as part of VISTA

sorry, i don't know what that is but you should find info about it somewhere on a vista forum....

20GB will be enough to start you with Ubuntu (more than enough)

you need to make sure that

1) your first partition is VISTA
2) create the free space at the end for Ubuntu


bren

---

