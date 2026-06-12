---
title: "Internet lag"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by myolbug on 2007-07-21
Hello, I apologize if this is a question that is often asked, but I don't even know how to do a search on it.  When I type a web address into the address bar, I get a lot of "looking for "'..."  and on some sites, a rather long delay.  

I don't have the fastest connection and this lag really slows things down.  This is the same on Firefox and Opera.  I am running Ubuntu6.06 LTS and my FF is 2.0 and Opera is 9.21.

My ISP uses the local phone company in a piggyback manner and they told me that it was a setting on my computer, and that basically my connection is going through the phone company network then to the site I am looking for then to me.  The help guy told me what it was, but I can't remember and he is not very knowledgeable about Linux.

Is this truly a setting on my computer, or should I go to the cable company and use them?

---

### Post by Al3xK3aton on 2007-07-21
> **myolbug said:**
> I don't have the fastest connection

A slow connection is a slow connection, no matter what your ISP says. I suggest earthlink.

---

### Post by myolbug on 2007-07-21
No can do, it's not offered here.  I have a 1.5Mb down and 512k up.  As far as downloading things, my connection is what is advertised, sometimes a little faster.  It is the annnoying Looing up lag that I want to get rid of.

---

### Post by rillip on 2007-07-21
What you're seeing are lame nameservers I think.   It's having to do DNS querries and the first nameservers you are hitting are slow to respond/forward the request.

Here's what happens:

You type ubuntuforums.org in the browser window
Computers don't know domain names, they know IP addresess, so it has to turn ubuntuforums.org into one.
First it asks itself if it knows (in this case it probably does; I imagine you don't see this as much on sites you frequently visit).  If it does, it just goes there.
If it doesn't, it asks your nameservers.  It finds these automatically usually when getting the IP address.  I think this is where the issue you're seeing is happening.

Your computer doesn't know, so it asks the ISP. Their nameservers are taking a long time to give the information back and/or send on the request, so your computer says "looking up..." while it waits.

You may be able to reduce the symptom by increasing your dns cache (not sure how this is done, but know it can be), but you can't get rid of it unless you switch to a provider that has a better nameserver.  If I'm right.

---

### Post by RomeReactor on 2007-07-21
Hi. Disabling IPv6 may help you with that problem: You'll need to modify a text file for this, so open a terminal (Applications->Accessories->Terminal) and enter:
```
gksudo gedit /etc/modprobe.d/aliases
```
that will bring up the text file with administrator privileges so you can modify it (aliases being a system file, belongs to root). Now, look for this entry
```
alias net-pf-10 ipv6
```
it should be line 17, or just above or below. You need to add a **#** at the beginning of the line (that is what people here refer to as "commenting" out a line, so the system disregards it as a comment and not as an actual command or setting). The line must then look like this:
```
#alias net-pf-10 ipv6
```
now you'll add another line to take its place; you don't want to delete the previous line, so that's why you comment it out. Now the line you need to add (preferably just below the one you modified) looks like this:
```
alias net-pf-10 off
```
now save the file, close the text editor, and reboot. You should experience a slight increase (or significant, your mileage may vary) in speed while surfing.

If this doesn't work for you, or you experience adverse results, you can open the text file again (**gksudo gedit /etc/modprobe.d/aliases**), delete the newly added line (**alias net-pf-10 off**), uncomment the previous one (so it ends up reading **alias net-pf-10 ipv6**, just like before you commented it), save the file and reboot.

---

### Post by myolbug on 2007-07-21
Thanks, Rome, this seems to have solved the prob.

---

### Post by myolbug on 2007-08-20
Well, after having run the changes that Rome suggested, it seems to have helped and not.  I think that I am suffering from what Rillip said.  I am going to call my ISP and see if they can do anything.  I'll keep all posted.

R:(

---

