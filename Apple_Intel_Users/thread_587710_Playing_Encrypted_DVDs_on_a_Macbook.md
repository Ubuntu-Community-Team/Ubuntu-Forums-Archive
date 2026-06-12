---
title: "Playing Encrypted DVDs on a Macbook"
date: 2007-10-23
forum: Apple Intel Users
---

### Post by falt004 on 2007-10-23
Hi,

I'm recently installed Kubuntu 7.10 on a new Macbook and everything went smoothly. The only problem is that I'm unable to play encrypted DVDs with Linux while unencrypted ones play just fine. libdvdcss is installed and the dvd's region is set to region 2 (which is also the DVD's region - not like the particular region should matter that much though)

The DVD in question works in OS X, and also on a desktop pc (which has Kubuntu 7.04 installed).

To try and figure out the problem, I ran kaffeine in verbose mode (kaffeine --verbose DVD), a file with the full output is attached to this post.

Any ideas why it's not working? Thanks

Cheers,
/Fuad

---

### Post by mcdull2k on 2007-10-23
There should be no legal DVD Player that will play encrypted content.

---

### Post by falt004 on 2007-10-23
The legality of this issue depends on the jurisdiction, I'm only concerned with the technical aspect for the time being :)

---

### Post by cyberdork33 on 2007-10-23
> **mcdull2k said:**
> There should be no legal DVD Player that will play encrypted content.

Apparently, what 'should' be and what is are two different things. It looks like decss is decrypting the dvd... (or at least it thinks it is), but you are getting some errors in the actual playback. Are you sure ou have the correct codecs installed?

---

### Post by falt004 on 2007-10-23
Thanks for your reply.

I'm as sure as I can be that I have the right codecs :) They're the same ones that I have installed on the desktop machine (the one I mentioned in my original post). They are:-

libdvdread3 libxine1-ffmpeg and libdvdcss2 (from medibuntu). Pretty much following the instructions at:-

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

That seems to work fine on the desktop machine, but not on the macbook...

Any ideas or suggestions?

Cheers

---

### Post by mike555 on 2007-10-27
== install VLC player and try it ===

---

