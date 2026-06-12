---
title: "Synaptic problems"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by Cod on 2006-07-03
Hi,
Complete newbie to Linux.  I've managed to install it and also got Firefox connected to the internet.  But when I try and use Synaptic I get "Could not download all repository indexes" and a list of failed connections.

Skimming through the forum I can see that I am not the first person to encounter this.  However, none of the fixes in other posts work for me.

I have added more repositories by clicking on the "add community maintained" box in the add repositories options of Synaptic but no joy (strangely whenever I go back to the add repositories menu, the box is unticked again.  Is this a bug, or has the ticked box not been recognised?).

I suspect that the problem is that I'm at work and need to set up my proxy settings.  I added them in Firefox (which I'm using now).  I also added my proxy settings to the  Synaptic network preferences.  No joy.  I added them to System -> Preferences -> Network proxy.  No joy.  Following another post I tried editing the apt.conf to include my proxy settings but.... no joy.

Can anyone help?  I am a total beginner with Linux so be gentle with me.

---

### Post by Jagot on 2006-07-03
Have you tried this?

[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)

---

### Post by Cod on 2006-07-03
Thanks for the suggestion but still unable to connect.  I got lots of lines like:

"Err [http://archive.blah.blah](http://archive.blah.blah)
  407 Proxy authentification required"

So it looks like my proxy settings need sorting out.  I've tried setting them in Synaptic but no success.  Any ideas?

---

### Post by lamego on 2006-07-03
Your proxy requires user authentication, apt does not understand it and will not prompt you for the user/pass .
You can workaround this by putting the user/password on the proxy url.
On the proxy setting use:
  http : //user : [email]password@proxy.hostname.com[/email] : port
(Without the spaces)

---

### Post by Cod on 2006-07-03
Thanks.  I suspected it was an authorisation problem.  I tried putting my name and password into the proxy address in:

Synaptic
apt.conf
both Synaptic and apt.conf

but to no avail - just the same error whether I try Synaptic or try aptitude update

I don't know what else to try....  What should the proxy under Preferences -> Network Proxy be?

---

### Post by lamego on 2006-07-03
The Preferences -> Network proxy are for gnome apps, it will not affect APT or synaptic.
For the apt/synaptic utilities the apt.conf will be used or the http_proxy environment variable.

---

### Post by Cod on 2006-07-03
Thanks.  Here is what I'm doing:

My apt.conf currently reads:

"Acquire::http::Proxy "false";"

In Synaptic ->Settings -> Preferences -> Network I have selected Manual proxy and filled in the HTTP and FTP slots with:

myusername:mypassword@148.252.96.122         and the port is 80

This set up doesn't work.  Does anything look wrong to you?  Should my apt.conf also have the proxy settings?  Calling "sudo env|grep proxy" returns nothing.  Is this OK?

---

