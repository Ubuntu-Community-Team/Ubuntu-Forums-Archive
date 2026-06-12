---
title: "Changing cursor not working - Xcursor Selector"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-06-04
Hi,

System/Preferences/Cursor Selection

The program starts but it won't let me install a new cursor set.

In the program I click "+Install Theme", and navigate to the theme, eg "index.theme", click "ok" and I get the following error popup,

"Could not open "index.theme"
Achive type not supported".

Thanks.

---

### Post by %hMa@?b&lt;C on 2006-06-04
they can only be installed from the .tar.gz files

---

### Post by u.b.u.n.t.u on 2006-06-04
I have "ComixCursors-0.4.1.tar.bz2" and tried many different combinations and nothing works. The cursors are not added.

---

### Post by cyangecko on 2006-06-04
Hello,

I tried to install that exact cursor set that you said you were having problems with.  I also was unable to successfully install them.  I have used the gcursor program to install other cursors before and it worked just fine.  I am thinking it is a problem with the set itself and not the fact that you haven't done something correctly.

---

### Post by u.b.u.n.t.u on 2006-06-04
Hi cyangecko,

I have several cursor themes and none can be installed. 

Does the gcursor in Dapper even work or is it a bug?

---

### Post by cyangecko on 2006-06-05
I use the 3d Glass cursors.  I installed them using the gcursor menu and following this guide (in section 5 of the first post):  [http://www.ubuntuforums.org/showthread.php?t=77694&highlight=howto+eyecandy]("http://www.ubuntuforums.org/showthread.php?t=77694&highlight=howto+eyecandy")

Make sure to read the note at the end of that section, as that was also a complication for me at first.  Goodluck.

---

### Post by u.b.u.n.t.u on 2006-06-12
This still doesn't work.

Here is what I did.

1. installed gcusor with synaptic.
2. System > Preferences > Cursor Selection
3. click "install theme"
4. navigated to my desktop and click on "Chameleon-Anthracite-0.5.tar.bz2" and click "ok"

The file, "Chameleon-Anthracite-0.5.tar.bz2", is extracted into a directory. Nothing else happens.

At the webpage with the instructions,
[http://www.ubuntuforums.org/showthread.php?t=77694&highlight=howto+eyecandy](http://www.ubuntuforums.org/showthread.php?t=77694&highlight=howto+eyecandy)

they say,

"NOTE: If the cursor you have selected in gcursor don't appear in the menu then press the Go To Theme Folder button, click the folder named after the cursor. There should be a new folder with the name of you cursor in there. Right click it and choose cut. Press the Up button in your file browser and Paste the file here. That should do the trick."

Well the cursor package I extracted into a directory does not appear in "Xcusor Selector". So their instructions, steps 1 to 4 don't work.

What does the following mean in plain English?

"There should be a new folder with the name of you cursor in there. Right click it and choose cut. Press the Up button in your file browser and Paste the file here."

What would an example be? Right click "it"? "It" what? The folder, a file? What folder? What file? The instructions are confusing at best, at worse, they don't work.

If anyone knows how to install a cursor theme in ubuntu 6.06 please reply.

Thanks.

---

### Post by u.b.u.n.t.u on 2006-06-14
If someone would please  walk me through the process of installing cursors that would be appreciated. Everything I tired has failed to work.

Thank you.

---

### Post by benjaminzsj on 2006-06-16
Hi. I seem to have solved this problem. It's not because the gcursor is malfunctioning, but the ComixCurcors has so many themes in it. So when you choose to install Comix in gcursor, the latter just extract the tar. Then you can copy all the folders with the corresponding names or any one you favor to the .icons/ folder in your home folder, afterwards you can find your cursor themes in gcursor as well as in mouse preference.
I installed the neutral theme with gcursor right out of the box, no problem at all.

---

### Post by u.b.u.n.t.u on 2006-06-16
I have tried so many times with different cursor themes and approaches, and failed, that I now just need clear step by step instructions to what actually does work.

I don't mind installing any cursor theme, just to see how this is supposed to work.

Thanks.

---

### Post by graigsmith on 2006-06-16
ok. here's how i got my x11 cursors working. 

1 open your home folder.
2 create a folder called '.icons'
3 the dot in front of it makes it a hidden folder, hit ctrl-h to show all the files
4 open the .icons folder.
5 extract your icon themes into that folder. 
6 open the mouse preferences, and pick whatever cursor you want.

this same method, including the .icons folder also works for icon themes.

---

### Post by u.b.u.n.t.u on 2006-06-16
Thank you graigsmith!

=D> 

I never put the cursors in the ".icons" folder. If I missed reading that previously then I don't know where, as it is news to me. Thank you again and for those doing a search I have elaborated on what needs to be done.

[COLOR="DarkOrange"][SIZE="2"]Install a Cursor theme - plain English tutorial.[/SIZE][/COLOR]

To install a cusor theme just place the cursor theme folder into the ".icons" folder:

/home/yourname/.icons

Then start,

System > Preferences > Cursor Selection

All the cursor themes show automatically.

* The cursor theme must not be more than 1 folder deep. It needs to be ".icons" folder and then "yourcusors" folder with all the contents there.

---

### Post by octathlon on 2006-07-16
This does NOT work for me! I've tried everything mentioned here and some things that weren't. I extracted the cursor theme folder into my ~/.icons directory, but it doesn't show up in gcursor (because it's a hidden folder, I suppose).

Also if I go to mouse preferences on the gnome menu, the cursors also don't appear there, which it sounds they should automatically be there according to the last 2 messages before mine, because their folder is in the correct directory.


======== rant follows ========
in fact I've tried doing a lot of "simple" things since installing Ubuntu, and with every single one of them I've had serious problems, even after carefully reading lots of instructions and threads.  Only one of these things (getting sound to work in Flash) have I actually successfully accomplished.  We should not have to work and suffer so much to accomplish such simple goals. :cry:  After a week of pain, I am about to give up on Ubuntu(and I've worked in the computer field for > 20 years, including on unix). Also, most programs I have tried locked up or crashed. The panel crashes every time I start gcursor or gconf-editor, etc.  gedit crashes when I try to use scim, etc. Sure, the OS doesn't crash; just all the apps.
And believe me, I really really want this to work, because I actually really like Ubuntu in spite of it all.  Oh, one thing did work right on the first try and that was adding the US-international keyboard.

---

### Post by orb9220 on 2006-07-16
Ok I found out how to make it work the cursor folder MUST! Have in it's folder a index.theme file and a folder called cursors.

They do not come that way.
Example Premium and two sub folders premium and premium-left select both and copy or drag to .icons then delete the folder you just got those from.

Check each folder in .icons whatever thier names and make sure they have a index.theme file and a folder that is called cursors,

Some of them even have a default folder where the index.theme file is I copy it and put it in with the folder with the cursor folder and walla it works.

Don't Ask Me Why I don't come from theis planet!

](*,)

---

### Post by octathlon on 2006-07-16
I have no idea why, but the cursor theme I downloaded is now working.  I copied the folder into .icons again, and this time it showed up on the list.  There isn't a file called index.theme in it though! BTW, what is supposed to be in the index.theme file?  

No idea what's going on.  I'll try downloading another one and see what happens.

Update:  I understand what I did wrong now. The cursor theme came in a folder called "contrastlarge" and inside that folder was another called "cursors".  The first time I extracted only the folder called "cursors" into the ~/.icons folder, not realizing it was only a subfolder. The second time I correctly extracted the entire "contrastlarge" folder into ~/.icons/  and then the theme automatically appeared in my mouse preferences dialog.  Hope that helps someone.

---

