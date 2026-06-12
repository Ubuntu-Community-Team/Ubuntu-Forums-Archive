---
title: "Download update from other computer??"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by mikeescott on 2007-02-20
I have grub working after another install and I have about 300mb of update to go through. On dial up, that take a few days getting disconnected every few hours. Is it possible to download the updates on the Windoze computer at work?

---

### Post by nereid on 2007-02-20
Sure, just put the downloaded *.deb files in /var/cache/apt/archives/.

---

### Post by mikeescott on 2007-02-20
How do I find the updates and their addresses that I need to download?

---

### Post by nereid on 2007-02-20
Good question...You could manually note them down for each package (which would be an obivous pain in the behind to do for such a giant update). But I think that there is a way to get  a list of all packages and their addresses. In the worst case you have to write yourself such an application, but I am really sure that such a kind of program does exists.

---

### Post by edwardLS on 2007-02-20
I hope this may be as much help to you as it has been to me.  I have a very similar situation; that is, I have a strategy of "download-at-work(Broadband)-install-at-home(dialup)".

I am using ubuntu (Dapper) and Synaptic Package Manager to do the following:  So far it has worked like a charm.

- With my dialup installation, I "Update" the repositories synaptic.
- When I have selected the updates/packages, I click (in Synaptic) File -> "something to the effect of Generate Download Script."  I have that script created on a USB Pen drive.
-I take the Pen Drive to work, and in Windows I edit the script file to remove the reference to the shell, and rename the script to something.bat - so I can execute in on windows.
- You will need to get and install on your windows machine a program called "wget".  I can't remember where I got it, but I found it pretty quickly.
- In windows with a DOS window I navigate to the Pen drive and the directory where the script is located.
-  Execute the something.bat file.
- Take the Pen Drive home, and in Ubuntu with Synaptic running, I go again to the File -> "something to the effect of add downloaded packages."
- Navigate to the Pen Drive and directory containing the downloaded packages, and select OPEN.
- Sit back and watch them install.

Hope this helps.

---

### Post by mi_were on 2007-02-20
> **edwardLS said:**
> I hope this may be as much help to you as it has been to me.  I have a very similar situation; that is, I have a strategy of "download-at-work(Broadband)-install-at-home(dialup)".

I am using ubuntu (Dapper) and Synaptic Package Manager to do the following:  So far it has worked like a charm.

- With my dialup installation, I "Update" the repositories synaptic.
- When I have selected the updates/packages, I click (in Synaptic) File -> "something to the effect of Generate Download Script."  I have that script created on a USB Pen drive.
-I take the Pen Drive to work, and in Windows I edit the script file to remove the reference to the shell, and rename the script to something.bat - so I can execute in on windows.
- You will need to get and install on your windows machine a program called "wget".  I can't remember where I got it, but I found it pretty quickly.
- In windows with a DOS window I navigate to the Pen drive and the directory where the script is located.
-  Execute the something.bat file.
- Take the Pen Drive home, and in Ubuntu with Synaptic running, I go again to the File -> "something to the effect of add downloaded packages."
- Navigate to the Pen Drive and directory containing the downloaded packages, and select OPEN.
- Sit back and watch them install.

Hope this helps.
I wish I knew about your simple work around when I had to download updates similarly! Great fix

---

### Post by dwblas on 2007-02-20
Can you boot a machine at work from the live CD or Knoppix and use the download script from the previous post?  Copy to pen drive or CD and update at home.

---

### Post by edwardLS on 2007-02-21
> **dwblas said:**
> Can you boot a machine at work from the live CD or Knoppix and use the download script from the previous post?  Copy to pen drive or CD and update at home.

I have not attempted this, but I don't see any reason why it would not work.  What I have done at work is use the script in both Windows XP (MS-DOS command prompt) and in Ubuntu (Dapper).  I have a dula-boot system at work.

In the case of using it in the command prompt of Windows, you must first delete the very first line in the script which refers to the Linux BASH shell.  In ubuntu you leave that first line alone.  I have had very good success with both download; i.e. Windows XP and Ubuntu.

---

### Post by edwardLS on 2007-02-21
> **mi_were said:**
> I wish I knew about your simple work around when I had to download updates similarly! Great fix

I must not take credit for this simple work around.  I gained the knowledge through these forums.

---

