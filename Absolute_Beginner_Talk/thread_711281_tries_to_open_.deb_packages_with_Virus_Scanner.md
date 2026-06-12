---
title: "tries to open .deb packages with Virus Scanner??"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2008-02-29
When I click to download a .deb package, it asks you what you want to do - "Open with", "Save to disk" etc. And the "Open with" should be "GDebi Package Installer". Right?
My problem is that every once in a while, the "Open with" is "Virus Scanner". Sometimes, trying several times brings GDebi back, at other times I have to wait a while and try again
Why is this happening? How do I fix it?

---

### Post by lswest on 2008-02-29
just choose GDebi from the drop-down menu next to "open with", seems a strange thing to have happen, but i don't know, did you install anti-virus software on Ubuntu?  might be happening because the virus software and GDebi are competing for rights to the file extension (e.g. the default program to open .deb files)

---

### Post by kleo skywalker on 2008-02-29
> **lswest said:**
> just choose GDebi from the drop-down menu next to "open with", seems a strange thing to have happen, but i don't know, did you install anti-virus software on Ubuntu?

There is nothing in the drop-down menu (would I be posting if there was!). Just "Other" and clicking that takes me to my home folder.
I haven't installed any extra anti-virus software. I can't remember for sure but I might have installed the GUI for the default one (Virus Scanner shows up in my Applications-->Accessories menu).

---

### Post by lswest on 2008-02-29
GDebi should be in your /usr/bin folder, if you can find it in there through "other", at least, theoretically, i'm guessing at it's location, but what you can also do is edit the default program to open .deb files with and remove and programs in the list apart from GDebi (right-click a .deb, properties, then under "open with" or so), should get firefox to see GDebi as the only file able to open .deb files, otherwise, just save to disk and then install it, i find it useful to keep .debs sometime anyways

---

### Post by kleo skywalker on 2008-03-01
> **lswest said:**
> GDebi should be in your /usr/bin folder, if you can find it in there through "other", at least, theoretically, i'm guessing at it's location, but what you can also do is edit the default program to open .deb files with and remove and programs in the list apart from GDebi (right-click a .deb, properties, then under "open with" or so), should get firefox to see GDebi as the only file able to open .deb files, otherwise, just save to disk and then install it, i find it useful to keep .debs sometime anyways

The default application is already GDebi Package Installer (I saved the .deb to disk, and checked in Properties). It still shows up as Virus Scanner when I click the link on the webpage though.

---

### Post by lswest on 2008-03-01
Hmm, very strange, i honestly don't know.  And I'm also curious as to what Virus Scanner that is, because honestly, you don't need one in Linux unless you're going to be using it to check files being sent to windows PCs, or a windows partition.  Maybe someone else will know the answer to this.

---

### Post by kleo skywalker on 2008-03-02
> **lswest said:**
> And I'm also curious as to what Virus Scanner that is

It's the default anti-virus thingy in Ubuntu - ClamAV or ClamTK whatever it's called.

---

### Post by Anduu on 2008-03-02
Right click on a .deb file and select properties.
Go to the Open With tab.
Make sure GDebi is selected and remove any other entries.Hopefully this will solve all the fighting ;)

---

### Post by billgoldberg on 2008-03-02
> **kleo skywalker said:**
> It's the default anti-virus thingy in Ubuntu - ClamAV or ClamTK whatever it's called.

There is no default anti-virus scanner in ubuntu.

---

### Post by kleo skywalker on 2008-03-03
> **Anduu said:**
> Right click on a .deb file and select properties.
Go to the Open With tab.
Make sure GDebi is selected and remove any other entries.Hopefully this will solve all the fighting ;)

Uh, read previous posts for what happens when I do that.

---

### Post by kleo skywalker on 2008-03-03
> **billgoldberg said:**
> There is no default anti-virus scanner in ubuntu.

I think you're right, in which case I probably installed ClamAV and ClamTK (it's  GUI front-end) from Synaptic. That's what Virus Scanner is.

---

