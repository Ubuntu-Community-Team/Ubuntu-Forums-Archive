---
title: "dialup worked on 6.06 but not 6.10"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by the.phantom on 2006-10-31
i have a hard drive with 6.06 and all works great
i just installed 6.10 on a new hard drive 
and having a cockpit trouble i think ;-)

in 
admin/networking  i have it set right

on 6.06 i clicked "activate: and it would dial

on 6.10 i click the check box ( per instructions in help)

and nothing happens no error and no dial?

i just need it working long enough to get kppp installed
and believe me i have been through all the settings i know several times

so can someone tell me what i am doing wrong
OR
a way i can use my XP to download kppp from somewhere and how to install it? if a deb i think i can do it?

thanks for any help !

---

### Post by qscgz on 2006-10-31
Give the **gnome-ppp** tool a trial :KS

[http://packages.ubuntu.com/edgy/net/gnome-ppp](http://packages.ubuntu.com/edgy/net/gnome-ppp)

[http://packages.ubuntu.com/edgy/net/kppp](http://packages.ubuntu.com/edgy/net/kppp)

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

found with [https://wiki.ubuntu.com/FindPage](https://wiki.ubuntu.com/FindPage)

---

### Post by D10 on 2006-10-31
I had the same problem in Xubuntu 6.10 when I upgraded. What I did was edit the /etc/wvdial.conf script, added the phone number, user info, and modem port. Also delete the ";" to remove comments. 

Then from a terminal just type wvdial and you should be able to dial out.
You should then be able to download kppp, or any other dialer app you choose.

Hope this helps.

---

### Post by GozzoMan on 2006-11-02
Hi all,
   I have the same problem (all ok in Dapper, no dialing at all in Edgy). I haven't tried wvdial yet, but I'm rather positive it will work.

Nonetheless, my point is: I think this is very nasty for the (mythical) Average User, I really think dial-up should work out-of-the-box with the beautiful GUI tool provided in the desktop CD (or else insert gnome-ppp into the cd and make it the "standard way" to connect, why provide network-admin instead if it doesn't work so often?? One release no fuss, the next *pam* broken again). While trying to do some proselitism to spread Ubuntu use among friends and colleagues, this has proved to be a major drawback! (This is not the first release with very similar problems.)

Among all the things that could go wrong, being unable to connect to the internet is one of the worst from a common user's point of view, because he is "left alone". Even is he's willing to explore and understand how things can be corrected, how is he supposed to know he can try wvdial if he can't read the forums?](*,) 

Just my respectful 2 cents,

---

### Post by GozzoMan on 2006-11-02
I'm trying to follow the thing on launchpad, but I'm not sure of what I'm seeing.

The bug is this one, isn'it?

[https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/22119](https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/22119)

While the corresponding on bugzilla (upstream?) seems to be this one. Again, am I correct?

[http://bugzilla.gnome.org/show_bug.cgi?id=316989](http://bugzilla.gnome.org/show_bug.cgi?id=316989)

Here the status is RESOLVED and resolution NOTGNOME... (Does this mean that the problem is not in the gnome package and hence someone else should take care? Who? Another not-gnome-related bug has to be filed? Where?) I added a comment on launchpad reporting that it's still present in Edgy final, should I do something else to signal the problem? Is that the proper place to file the issue?

Thank you all,

---

### Post by the.phantom on 2006-11-03
thanks i used the gnome-ppp and worked great
just had to tell it i am ttys3
still like kppp for the status graph but that is one of those "in the future" things ;-D

---

### Post by GozzoMan on 2006-11-23
> **GozzoMan said:**
> I added a comment on launchpad reporting that it's still present in Edgy final, should I do something else to signal the problem? Is that the proper place to file the issue?


For anyone else looking for the solution, on launchpad I had a few interesting answers (thank you, Konstantinos and Carlos) that I report here:


>  
Re: [network-admin] Dial out does not work from Konstantinos Tampouris at 2006-11-15 22:02:03 UTC

In Edgy this is caused by incorrectly setting the dial-out command to "ATDTW" or "ATDPW" instead of "ATDT" or "ATDP" in /etc/chatscripts/ppp0.


Re: [network-admin] Dial out does not work from Konstantinos Tampouris at 2006-11-17 11:29:33 UTC

The quick and dirty way to fix things for Edgy: Go to file /usr/share/system-tools-backends-2.0/scripts/Network/Ifaces.pm, line 3137 (subroutine get_interface_replace_table, section "debian-3.0") and remove 'W' from between %external_line% and %phone_number%.


Re: [network-admin] Dial out does not work from Carlos Garnacho at 2006-11-17 12:17:58 UTC

The "W" issue is already fixed in system-tools-backends HEAD


A question about Carlos' comment: I presume system-tools-backends is a package, what does "HEAD" mean? The last release version? The last developement version?


Thank you all again,

---

### Post by Michl on 2007-03-23
For what it is worth, the problem continues in Feisty.   This seems to me to
be such a simple and important thing to fix.  As Gozzoman said earlier, this
is a serious stumbling block for the ordinary person.  I got through this hurdle
because I was committed to Linux come hell or high water, but a more
objective person with dial-up would throw in the towel right then and there.
I almost did.
Michael

---

### Post by Michl on 2007-03-23
> **GozzoMan said:**
>  should I do something else to signal the problem? Is that the proper place to file the issue?

Cristiano,
See:
[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/94304](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/94304)
and the last comment.  Also see,

[http://www.ubuntuforums.org/showthread.php?p=2344638#post2344638](http://www.ubuntuforums.org/showthread.php?p=2344638#post2344638)

If we want the dialup in networking-admin to work, we need to try to fix it.
Any ideas?

---

