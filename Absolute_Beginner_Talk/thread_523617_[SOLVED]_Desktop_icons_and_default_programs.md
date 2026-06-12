---
title: "[SOLVED] Desktop icons and default programs"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by Baby Boy on 2007-08-12
I've got two questions:

1.) How can I make desktop icons? Is that even possible? When I right-click on an item from the menu and select 'Add this launcher to desktop', nothing happens.
2.) I recently downloaded kpdf for reading .pdf files. But if I want to download and open a  .pdf file from Firefox immediately, there is only Document Viewer selected as default program for that action and when I click 'Other' I can't find the kpdf anywhere. I don't know where it's located and search doesn't help much. I need to know because I'll probably need it for other programs too.

---

### Post by RomeReactor on 2007-08-12
Hi. Just drag the items from the menu to your desktop. As for Firefox opening pdf files with Evince (Document Viewer), you could change that behaviour in Firefox, by going to "Edit->Preferences->Content->File Types" (press the **Manage** button), highlight **pdf**, press "Change Action", and look for the kpdf pugin (if there's one available). In any case, what's wrong with using Evince's plugin to view embedded pdf files?

---

### Post by Baby Boy on 2007-08-12
> **RomeReactor said:**
> Hi. Just drag the items from the menu to your desktop. 
I get the message 'Error while copying to /home/<username>/desktop.
You do not have permissions to write to this folder'

> As for Firefox opening pdf files with Evince (Document Viewer), you could change that behaviour in Firefox, by going to "Edit->Preferences->Content->File Types" (press the Manage button), highlight pdf, press "Change Action", and look for the kpdf pugin (if there's one available).I go there but there is no 'pdf' file type which I can highlight.

> In any case, what's wrong with using Evince's plugin to view embedded pdf files?
Nothing, just heard kpdf is better.

---

### Post by RomeReactor on 2007-08-12
> **Baby Boy said:**
> I get the message 'Error while copying to /home/<username>/desktop.
You do not have permissions to write to this folder'
That is a significant error. What's your computer's userrname? If you're unsure, please post the output of running this command in the terminal (Applications->Accessories->Terminal):
```
pwd
```

---

### Post by Baby Boy on 2007-08-12
> **RomeReactor said:**
> That is a significant error. What's your computer's userrname? If you're unsure, please post the output of running this command in the terminal (Applications->Accessories->Terminal):
```
pwd
```
:lol: I was stupid to post that '<username>' thing, I didn't actually get *that* in the message, just my actual username, so it was something like this:
> Error while copying to /home/freeman/desktop.
You do not have permissions to write to this folder
I replaced my username in my previous post because I thought that might be confusing. Now I realize how totally unnecessary that was, sorry for that.

So, any ideas on the problem?

EDIT: The problem seems to be more serious that I had thought. I was downloading the UT2004 demo and when the download was finished I got a message saying it could not be saved to desktop because I can't change the contents of that folder, bla, bla, bla...What the heck is wrong? :confused:

---

### Post by lambros on 2007-08-12
> **Baby Boy said:**
> I get the message 'Error while copying to /home/<username>/desktop.
You do not have permissions to write to this folder'


Yes, that is a strange error.  Also, it's strange that your 'desktop' begins with a lower-case 'd'.  It's probably just a simple problem with permissions.  Just to confirm this, please post the output of this terminal command:

```
ls -ld $HOME/{D,d}esktop
```

Lambros

---

### Post by Baby Boy on 2007-08-12
> **lambros said:**
> Yes, that is a strange error.  Also, it's strange that your 'desktop' begins with a lower-case 'd'.  It's probably just a simple problem with permissions.  Just to confirm this, please post the output of this terminal command:

```
ls -ld $HOME/{D,d}esktop
```

Lambros
Here's what I get.

> ls: /home/freeman/desktop: No such file or directory
drwxr-xr-x 3 root root 4096 2007-08-12 11:05 /home/freeman/Desktop


EDIT: Also, there is a lock sign above my desktop folder, and when I right-click on it, under the Permissions tab I get this:
Owner: root
Group: root
You are not the owner, so you can't change these permissions.

'S that normal?

EDIT 2: Also, I can't seem to create, move to or from anything in desktop and I get this permissions message every time. Please tell me you know how to solve this.

---

### Post by lambros on 2007-08-12
> **Baby Boy said:**
> Here's what I get.



EDIT: Also, there is a lock sign above my desktop folder, and when I right-click on it, under the Permissions tab I get this:
Owner: root
Group: root
You are not the owner, so you can't change these permissions.

'S that normal?

No, but not to worry - this command should fix it:

```
sudo chown $USERNAME:$USERNAME $HOME/Desktop
```

If you're prompted for a password, type it in.  It won't be shown as you type it, but it still works.

Lambros

---

### Post by Baby Boy on 2007-08-12
> **lambros said:**
> No, but not to worry - this command should fix it:

```
sudo chown $USERNAME:$USERNAME $HOME/Desktop
```

If you're prompted for a password, type it in.  It won't be shown as you type it, but it still works.

Lambros
You're a genius, thanks mate :popcorn:.

---

