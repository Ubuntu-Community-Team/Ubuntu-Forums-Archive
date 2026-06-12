---
title: "&quot;BOINC Manager is not currently connected to a BOINC client.&quot;"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by Nemato on 2007-05-03
I am new in Linux; Ubuntu 6.10.
I installed Boinc, but can't attach a project:

"BOINC Manager is not currently connected to a BOINC client.
Please use the 'File\Select Computer...' menu option to connect up to a BOINC client.
To connect up to your local computer please use 'localhost' as the host name."

I tried:
Advanced; Select computer; Host name: localhost
Does not work. I have ADSL internet connection that so far worked without problems.

---

### Post by - Lazlo - on 2007-05-06
You have to first add an account to BOINC.

You should look on this page for more info: [http://boinc.berkeley.edu/trac/wiki/RunningBoinc](http://boinc.berkeley.edu/trac/wiki/RunningBoinc)

On which platform are you btw? Because BOINC does not work on AMD64.

---

### Post by Ian505 on 2007-12-26
I am having the same problem. I have an Intel Quad Q6600 CPU. I also get these messages about not being able to connect to the client. Mabye there is some Linux security feature that is blocking its connection? I trust it fully, so is there a way to remove the restrictions on BOINC?

I am running Gutsy.

-Ian

EDIT- I found this... but it didn't help me.
[https://bugs.launchpad.net/ubuntu/+source/boinc/+bug/131986](https://bugs.launchpad.net/ubuntu/+source/boinc/+bug/131986)

---

### Post by coolbrook on 2007-12-28
Which version of BOINC are you running?  Consider uninstalling the repository version and try the latest (Ubuntu) version from Berkeley.

[http://boinc.berkeley.edu/download_all.php](http://boinc.berkeley.edu/download_all.php)

I'm running 5.10.21 without issue.  I created a launcher that points to BoincMgr.

---

### Post by jslmg on 2007-12-30
If BOINC is not working in your Ubuntu, what probably happened was that you installed "BOINC Manager" from Add/Remove Programs or Synaptic. You need to install "boinc-client."

Open a terminal and type:

```
sudo apt-get install boinc-client
```

and your password at the prompt.

You can also find it in Synaptic Package manager, which is no doubt easier.

After downloading the client, you'll automatically get a project selection dialog when you start the BOINC manager.

---

### Post by Ian505 on 2007-12-30
> **jslmg said:**
> If BOINC is not working in your Ubuntu, what probably happened was that you installed "BOINC Manager" from Add/Remove Programs or Synaptic. You need to install "boinc-client."

Open a terminal and type:

```
sudo apt-get install boinc-client
```

and your password at the prompt.

You can also find it in Synaptic Package manager, which is no doubt easier.

After downloading the client, you'll automatically get a project selection dialog when you start the BOINC manager.

Yep, that was the problem! Thanks!

---

### Post by Eagle70ss on 2008-02-15
I second this solution!!

This was the problem on mine also...

Thanks!

---

### Post by rockhen on 2008-06-18
I get the prompt, but nothing is being typed when I try to put password in!

---

### Post by rockhen on 2008-06-18
Did it the Synaptic way and succeeded. Sorry to mither so quick, was frustrated.:)

---

