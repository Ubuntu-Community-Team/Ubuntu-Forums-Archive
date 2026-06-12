---
title: "Forum OK for servier questions?"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by srk3nn3dy on 2007-05-27
Dear All,

I qualify as an absolute beginner in Ubuntu Linux, but my questions are server-related, some using command line interface.  I'd like to know, first, if this is an appropriate venue for these sorts of questions and, if so:

Using Ubuntu 6.10 

1) I have one server, in use in a test environment, on which when I reun useradd username, I am prompted for password, firstname, lastname and more, and it creates a /home/username directory, drawing the structure from the skel directory.  On my other server (that I'm trying to set up just like the first, my useradd only adds a user with no home directory, no PW prompt, etc. 

Can someone point me in the direction of an explanation?

2) If I want to create a user/user group that can add users and not do any other admin tasks.  What is the general strategy in Linux

3) In which configuration file does the hostname reside.  Is changing the machine name as simple as editing this file?  And is a reboot required after chaning the name?

Sincerely,

Ridge [in New Joisey]

---

### Post by irish_flu on 2007-05-28
Well, I can only help with your last question:

The hostname lives in a file at /etc/hostname  (hostname is the file name).

I'd reboot after I changed it, but maybe I'm old-skool.  You might be able to get away with restarting  networking services, I'm just not sure.  :)
restart networking with this command:
```

sudo /etc/init.d/networking restart

```

and yes, I think you're asking in the right place.  If nobody gets back to you here, you might try the "general help" area.

---

### Post by srk3nn3dy on 2007-05-28
Thank you very much.  R.

---

### Post by Bachstelze on 2007-05-28
1) *useradd* does not prompt for any info, *adduser* does.

2) You give that user/group sudo rights, but only on the comands you want.

3) /etc/hostname

---

