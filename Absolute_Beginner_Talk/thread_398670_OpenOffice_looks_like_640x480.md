---
title: "OpenOffice looks like 640x480"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by berftude_lives on 2007-04-01
Hi

I'm having problems with OpenOffice.  Basically, everything is huge.  The GUI elements and fonts are enormous, and the fonts (both GUI and actual typing) are bold.

I am able to set smaller toolbar icons and I can get the overall GUI *somewhat* under control by using the Scaling option, but it only goes down to 80%.  Plus, it makes things look stretched, so whatever it is I think it's the wrong approach.

The following screen capture is on a 1280x1024 display.  My other applications are fine.

[http://img526.imageshack.us/img526/7036/openoffice204wc6.jpg](http://img526.imageshack.us/img526/7036/openoffice204wc6.jpg)

I was only able to find one mention of this problem in the forums, and the person asking about it only mentioned the menus being large.  It looks like he didn't get any suggestions:  [http://ubuntuforums.org/showthread.php?t=327863]("http://ubuntuforums.org/showthread.php?t=327863")

> 
My fonts are okay for typing etc but the menu fonts are huge. Bad thing is Ive tried all the fixes I could find on the net and none worked.

You can see my fonts here.
[http://img174.imageshack.us/img174/2...apshot4sw3.jpg](http://img174.imageshack.us/img174/2...apshot4sw3.jpg)


Right now I'm most concerned with the GUI, but I won't be able to use OpenOffice without eventually getting the other issues resolved.  Thanks for your help.

---

### Post by bapoumba on 2007-04-01
Hello,
try to rename .openoffice.org2 and .openoffice (in your /home folder) with the _old extension. This may be a problem with your user conf files.
Or create another user (**sudo adduser <choose_a_login_here>**), login with that new user and check if you still have the same issue.

What is your default system font ?

---

### Post by berftude_lives on 2007-04-01
Thanks for replying.

I renamed the .openoffice2 directory.  I do not have a .openoffice file/directory.  Unfortunately I'm still experiencing the problem.

My default font is Sans 9.  There is a thread in this forum about OpenOffice ignoring the default system font, but I can't find it at the moment.

I created a new user.  This user did not have any of the problems I am experiencing.  On a whim I copied that user's .openoffice2 directory into my home directory.  That had no effect.  As with my "diseased" user, the new user did not have a .openoffice file/directory.

When I initially copied the .openoffice2 directory from the new user's home directory, I did it as sudo, so root owned the files.  That might have been a problem so I 777ed the new user's files and copied them again.  My bad user then showed as the owner.  I then did a recursive grep through the files for the old user name and replaced it with my bad user's.  There was only one entry: 
.openoffice.org2/user/psprint/pspfontcache:EmptyFontCacheDirectory:1175447742:/home/newuser/.openoffice.org2/user/psprint/fontmetric

What next?  :)


EDIT: expanded on cp openoffice2 section

---

### Post by berftude_lives on 2007-04-03
*bump*

Anyone?

---

### Post by bapoumba on 2007-04-04
Hello,
please post the way you installed OOo and the version you are using.
I'm trying to call in a friend of mine who knows much about OOo (whih I do not ;)).

---

### Post by Hagar Delest on 2007-04-04
Hi,

I remember having seen this issue somewhere, especially the new user without the problem but I can't find out the fix right now.

Here is a thread that may help : [How do I change user interface font (menus, etc)]("http://www.oooforum.org/forum/viewtopic.phtml?t=29952"). Using the font replacement table may help but nit sure. I'll try to dig my memory.

Are you using KDE ?

---

### Post by berftude_lives on 2007-04-04
Thanks for getting back to me.

_bapoumba_
I am using Open Office 2.0.4-ubuntu5.  I installed it from a terminal window with 'sudo apt-get install openoffice.org'.


_Hagar de l'Est_
I'm using Xfce on an  Edgy server install.  No KDE here.  I haven't installed Gnome desktop, either.  I know you didn't ask -- just trying to anticipate possible future questions since communicating over forums is slow.  :)  The font replacement worked (in that it is operational) but it didn't make anything smaller.

---

### Post by Hagar Delest on 2007-04-05
I've heard there is a setting for the Desktop where you can *Allow Xfce to manage the Desktop*. Is it checked ?

---

### Post by berftude_lives on 2007-04-05
Yes, it is currently checked.  Checking/unchecking seems to have no effect.

---

### Post by cypherzero on 2007-04-05
I also thought it looked huge when I ran it, I just assumed it was the Linux fonts compared to Windows. All the text in Linux is bigger giving the impression of lower resolution.

---

### Post by jordanmthomas on 2007-04-06
To fix my OOorg I had to disable "use system fonts" and scale the UI down in the Tools -> Options -> OpenOffice.org -> View

They're still not perfect, but they are better than they were before.

---

### Post by berftude_lives on 2007-04-06
_cypherzero_
It's not just the text.  You can see in the screen shot that the options window takes up more than half the screen at 1280x1024.

_jordanmthomas_
I appreciate your reply but as I said in my first post, I tried the scaling option and found the results not to my liking.  And as I said in a later post, new users do not have this problem so I should not *need* to use it.  Even if it made everything look fine, which it does not, it would only be masking the symptom of a persisting problem.

---

### Post by jordanmthomas on 2007-04-06
Sorry, I somehow missed that you had tried scaling.
I think the text is making the widgets bigger, which in turn makes the window bigger.  

I have one more thing you might be able to try:
In a terminal, type:
```
set | grep OOO
```
If it says that OOO_FORCE_DESKTOP=gnome, then ignore the rest of the post.

If nothing is returned, try running this:
```
export OOO_FORCE_DESKTOP=gnome
```
Then, launch OpenOffice and see if it helps any.  I know you're using xfce but maybe it will get its font information from your current settings anyway.

If nothing it *does* help, run this to make it permanent...though I'm still not sure why it works for new users.
```
echo "export OOO_FORCE_DESKTOP=gnome" >> ~/.bashrc
```

Just an idea anyway.

---

### Post by berftude_lives on 2007-04-06
Thanks for the pointer.  Sadly it had no effect.  This is getting crazy!  Let's think about what we know -- one user account has the problem.  Newly created accounts do not.  Config file problem?  Copying the "good" user's config files has no effect.

Does Open Office keep user-specific settings in a place other than the user's home directory?  This would go against common sense, but given the behavior I would not be surprised.

EDIT:  I could also try copying hidden directories from my bad user to my good user to see if I can mess up the good account.  I'll try that and post my results.

---

### Post by jordanmthomas on 2007-04-06
I can't find anything too great (ie nothing about why the other users worK), but I did find something that should help (it did for me at least):
> Changing the user interface font

There is no dedicated option to just change the font in the User Interface in OpenOffice.org versions that are based on the 641 builds (including OpenOffice 1.0). Nevertheless it is possible to change the font by the general font replacement mechanism. Select

        Tools -> Options -> OpenOffice.org -> Font Replacement
        

from the menu. Check the "Apply Replacement Table" check box. Replace the font

        Andale Sans UI
        

with the desired font. You probably will not find "Andale Sans UI" stated in the font list box of the font to be replaced but you have to write it manually into the "Font" field. Please choose one of the fonts from the dropdown list box for the "Replace with" entry. The settings apply immediately after pressing the "OK" button.
-- from [http://www.openoffice.org/FAQs/fontguide.html](http://www.openoffice.org/FAQs/fontguide.html)

I don't have Andale Sans UI installed, but I told OOorg to replace it with one I did have and it fixed my font problem.  Maybe this could serve as a temporary workaround for you?

---

### Post by berftude_lives on 2007-04-06
*sigh*

post #7...

---

### Post by jordanmthomas on 2007-04-06
OK, I obviously don't pay any attention so I'll leave you alone now.
Sorry.

**edit**  But, hey, at least mine looks better now.  :)

---

### Post by Hagar Delest on 2007-04-25
> **berftude_lives said:**
> EDIT:  I could also try copying hidden directories from my bad user to my good user to see if I can mess up the good account.  I'll try that and post my results.
Any news ?

If not, you could try to install the 2.2 version manually with the official OOo RPMs (several threads about that in this forum).

---

### Post by four100d on 2008-03-17
I too had the exact same problem with OpenOffice. I have Xbuntu 7.10 and HAD OpenOffice 2.3.0. I know this thread is a bit old, but I thought I would post anyway in case a few other people out there still have the same problem.

**I finally fixed the problem** by COMPLETELY removing all of OpenOffice using the Package Manager, then downloaded the latest OpenOffice version (2.3.1), then followed the instructions in the link below to manually convert the RPMs to DEBs, install the DEBs and install the menu items.

[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=398074[/COLOR]]("http://ubuntuforums.org/showthread.php?t=398074") 

Before you start, make sure MULTIVERSE is selected in your SOFTWARE RESOURCES because OpenOffice uses Sun JRE. 

Also, keep in mind that these instructions are for an older version of Open Office. So when following the instructions to install the menu items, you will have to go to the "desktop-integration' folder and get the name of the menu deb package for 2.3.1, the instructions from the post link should tell you where that folder is, if not, here is the deb file name for the menu:

**openoffice.org-debian-menus_2.3-9238_all.deb**

Hope this helps...

-Micah

---

### Post by Hagar Delest on 2008-03-25
Note that you don't need to convert the RPMs anymore since OOo is now delivered directly in .debs, see here: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

