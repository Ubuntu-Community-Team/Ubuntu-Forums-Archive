---
title: "[SOLVED] Cant open qbemail.pdf with (Evince) Document Viewer"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by iClouseau88 on 2007-11-03
Hi all,

I received from my ISP a Thunderbird e-mail with an attached invoice in the QuickBook format called qbemail.pdf. I cannot open the attachment with Gutsy Ubuntu's default Evince Document Viewer since it shows only the top part of the invoice, and the rest is blank. I then downloaded the .deb file of Adobe Reader and installed it using Synaptic Package Manager. Synaptic shows that the package is already installed, but when I right click to open the attachment nothing happens. I need your help. Normally when I run the Win XP part of my machine I can open the QuickBook attachments via Adobe Reader.

:confused:

---

### Post by Maestro23 on 2007-11-03
Adobe Reader is called acroread in the Repositories.  Might have a conflict between what you installed and acroread.

Can you uninstall the .deb you installed?

> sudo dpkg -P packagename

---

### Post by iClouseau88 on 2007-11-03
dpkg - warning: ignoring request to remove adobereader which isn't installed.
hoe1@hoe1-laptop:~$ sudo dpkg -P acroread
dpkg - warning: ignoring request to remove acroread which isn't installed.

---

### Post by Maestro23 on 2007-11-03
> **iClouseau88 said:**
> dpkg - warning: ignoring request to remove adobereader which isn't installed.
hoe1@hoe1-laptop:~$ sudo dpkg -P acroread
dpkg - warning: ignoring request to remove acroread which isn't installed.

If the name of the .deb was adobereader, then it didn't install.  Can you install acroread?

> sudo apt-get install acroread

If you don't find it, you will have to add the Medibuntu repo: [https://help.ubuntu.com/community/Medibuntu?highlight=%28Medibuntu%29](https://help.ubuntu.com/community/Medibuntu?highlight=%28Medibuntu%29)

---

### Post by iClouseau88 on 2007-11-03
Hi,

Close but no cigars!  I added Medibuntu repositories, installed "acroread" via Synaptic Pkg Mgr.  I then had some tough time locating this pkg, but eventually found it in /usr/bin.  I then made Thunderbird to download attachments via "acroread".  When I right clicked the attachment, Adobe Reader opens but it's mostly blank, with an initial blank dialog box entitled "Rebuild".  So the outline of Adobe Reader is there but the content or the invoice file is blank.

What should I do next?  Thanks in advance.

---

### Post by iClouseau88 on 2007-11-18
Hi everyone,

I installed acroread and am able to use either evince or acroread to read PDF documents when not using Thunderbird.  However,  when I open TB's attachments the error message reads to the effect Acrobat Reader cannot open attached document, etc. I foolishly removed "acroread" from Edit Download Actions (TB> Edit> Preferences>View & Edit Actions), because I was hoping to edit this window to put evince back on.  Now when I open the Download Action window it's empty and the 2 buttons called Remove Action & Change Action are greyed out! I no longer can choose either Evince or acroread to open PDF attachments. I checked but did not see Adobe being installed as a Firefox plugin. I saw the following instructions to install Adobe Reader plugin from Adobe webpage but they are not clear:

1. install adobe reader (done: acroread)
2. create a symbolic link to (?) nppdf.so to your Mozilla plugins directory (Note: in my PC: /root/.mozilla/plugins/nppdf.so). For this particular item, what's the symbolic link and from where to where, and how?
3. ensure a copy of acroread is in your PATH (what is this PATH?)

I would much appreciate your help in getting TB to read PDF attachments and installing Adobe Reader as a Firefox plugin.

---

### Post by iClouseau88 on 2007-11-19
Good news everyone,

Here's the solution from Maybelline8 of Adobe Reader for Linux Forum:

Try this:
1. Install "Mime Edit" from [https://addons.mozilla.org/en-US/thunderbird/addon/4498](https://addons.mozilla.org/en-US/thunderbird/addon/4498).
2. Restart Thunderbird
3. Go to menu Tools->MIME Edit...
4. Go to Edit tab and click "New Type" button
5. In "MIME type" and "Extension" textfields, type "PDF".
6. Select the radiobutton "Open it with" and choose the path of acroread application by clicking the 'Choose' button.
7. Click OK on all open dialogs and restart Thunderbird.

Now you check Edit> Preferences>View & Edit Actions. You should be able to see the PDF association with acroread.

PS: I should add we need to associate image (jpeg) files with Ubuntu's default Document Viewer called Evince (Browse > /usr/bin).

---

