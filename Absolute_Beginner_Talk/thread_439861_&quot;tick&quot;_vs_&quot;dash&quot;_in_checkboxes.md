---
title: "&quot;tick&quot; vs &quot;dash&quot; in checkboxes"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by lockherin on 2007-05-11
Hi, after I installed a fresh copy of ubuntu 7.04, I then go the synaptic package manager. Then I select "Settings" --> "Repositories" and the "Software Sources" box pop up.

At the "Ubuntu Software" tab, I saw the first four checkboxes are ticked, but the fifth check box "Source code", there is a dashed sign inside. All the five checkboxes are colored.

Then, when I click on the "Updates" tab, I saw that the first checkbox is ticked, but the 2nd checkbox "Recommended updates" has a dashed sign inside. Both checkboxes are colored.

What is the difference between "ticked" and "dash sign" in the checkboxes?

I have included 2 jpg attachments for reference.

Thanks!

---

### Post by octoberdan on 2007-05-11
**Edit:** Sorry, misunderstood what you were asking

---

### Post by Cypher on 2007-05-11
Try ALT-F2 and type
```

cat /etc/apt/sources.list

```
and show us what the output is..

---

### Post by lockherin on 2007-05-14
I did what you advise and click on the "Run" button, but nothing happened after that.
Attached is the image.
I am running ubuntu inside vmware


> **Cypher said:**
> Try ALT-F2 and type
```

cat /etc/apt/sources.list

```
and show us what the output is..

---

### Post by Cypher on 2007-05-14
Select the "Run in terminal" option..

---

### Post by srt4play on 2007-05-14
> **Cypher said:**
> Try ALT-F2 and type
```

cat /etc/apt/sources.list

```
and show us what the output is..

Uh, that's not going to work.  Maybe you meant ALT-F2 and type 'gedit /etc/apt/sources.list'?

OP:  I'm curious myself what the difference is between a 'tick' and a 'dash'.

---

### Post by lockherin on 2007-05-16
I type ALT-F2 and type "cat /etc/apt/sources.list" with the "Run in terminal" option, but nothing happen.

Then I try ALT-F2 and type 'gedit /etc/apt/sources.list' and something appears. It's in the screen shot attached.

So what's the difference between "ticked" and "dash sign" in the checkboxes?

---

### Post by kaamos on 2007-05-16
What he was probably leading you to was that a dash means that some of the repositories are in use and a tick means that all of them are in use.

---

### Post by rich.bradshaw on 2007-05-16
Tick means it's being used, dash means that it is in your list but commented out I think.

---

### Post by srt4play on 2007-05-16
> **kaamos said:**
> What he was probably leading you to was that a dash means that some of the repositories are in use and a tick means that all of them are in use.

I think I might agree with that, dash means that all repositories for that category exist in the sources.list file but not all are activated (uncommented).  I'm still not entirely sure though.

---

### Post by srt4play on 2007-05-16
A related note that I think should be pointed out is the Synaptic Help is quite broken.  It references menus that don't exist as well as the repositories settings screen is completely different.  Does Ubuntu work on those Help files or are they just brought down from Debian and not checked?

---

