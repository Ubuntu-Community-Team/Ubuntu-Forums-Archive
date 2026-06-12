---
title: "Synaptic Warning"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by G-Prime on 2007-01-11
I went to press "reload" on synaptic today and when I did I got a warning saying 

W: GPG error: [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

I also get the exact same error when I run "sudo apt-get update" in the terminal

Can someone please explain to me what this error means and how I can fix it?

attached is a screen shot of the error incase I did not properly explain the problem
[IMG]http://i34.photobucket.com/albums/d110/mixolydian/Screenshot.png[/IMG]

---

### Post by jem7v on 2007-01-11
It means that the Wine repository does not have a signature verified with your computer; i.e., it's warning you that there's the potential for said repository to be carrying unsavory programs.  It'll say that about any repository you add without adding the GPG key.  Most repo sites will have instructions on how to do that on the site, but I don't see the instructions on the Wine site.  You might be able to find the instructions is you look harder than I did (which is to say: I glanced).

But because it's Wine and you know what the site is, you can probably trust them.  It's more of a security Warning than an Error.

---

### Post by G-Prime on 2007-01-11
ohhh that makes sense; thanks for helping and explaining :)

---

