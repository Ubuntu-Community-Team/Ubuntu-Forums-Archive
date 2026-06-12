---
title: "Trying to get networking configured properly"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by DPhil on 2008-04-19
I am new to Linux, but a  proficient Windows user.  I have installed Ubuntu 7.10 on a box to support a few applications. And it's been great so far.

I have 2 related problems:

1. I need to be able to access the web server on the box using the machine name (Linux1).  I have installed Apache2 and it all works fine, except I can only access web pages using the IP address, which is not very friendly.  What have I missed?

2. I have setup file sharing with Samba, configured it so the workgroup is the same as my windows workgroup.  When my windows machine scans the network it shows the box as Linux1, But when I try to access it it says "Windows cannot access Linux1".  I have setup the smb share password and tried troubleshooting it, but no luck.

So do I have a problem with the machine name not resolving somewhere?  I'm not sure what I am missing.

Thanks for any help......

---

### Post by paydaydaddy on 2008-04-19
Check out this tutorial:
[http://ubuntuforums.org/showthread.php?t=202605&highlight=stormbringer](http://ubuntuforums.org/showthread.php?t=202605&highlight=stormbringer)
Using this guide I was able to get samba working.

---

### Post by chlorinekid on 2008-04-19
this video helped me loads in setting up samba [http://youtube.com/watch?v=Ad17kma8rNM](http://youtube.com/watch?v=Ad17kma8rNM)

might help you with your second point..

---

### Post by DPhil on 2008-04-19
Thanks guys...I'll check those out and let you know how I get on.

---

### Post by DPhil on 2008-04-19
I followed both of those, still no joy :(

The windors Explorer browser finds the Linux1 box, but when I select it, it says it is not accessible or may be an invalid path.

I have been fairly careful...the only thing I'm not sure about is the Samba user names - I set a user with the same login name and password as my Windows box - but just the username, not "machinename/username".  Is this right?

Any other ideas?

---

### Post by DPhil on 2008-04-22
I found the cause of both problems - I hadn't allowed ports 135-139 and 445 on the firewall.

I anyone follows the tutorials and still gets no joy, try the firewall!  I guess the tutorials all assume that there is no firewall running.

So all is working well now.

---

