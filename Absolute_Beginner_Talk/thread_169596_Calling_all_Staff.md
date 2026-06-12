---
title: "Calling all Staff:"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-05-02
Please make a sticky with  this website: [http://monkeyblog.org/ubuntu/installing.html]("http://monkeyblog.org/ubuntu/installing.html")
because so many new ubuntu users have trouble with this.
you might want to call it:
"New to Linux? Need to know how to install programs?" or a variant

---

### Post by nanotube on 2006-05-02
a comment:
in the part about installing stuff from source
instead of recommending "make install" i suggest that you recommend using "checkinstall". checkinstall is available from the repositories, and what it does is automagically create a .deb file, and install it - that way you can later uninstall with synaptic, without having to rely on "make uninstall", which may not even be present!
and btw, great install guide! i will link to it in my sig, cuz there are always people asking how to install stuff. :)

---

### Post by Raavea on 2006-05-02
Yeah, I found that guide very handy when someone linked me to it. It went straight in my tabby-bookmarks! ^__^

---

### Post by nanotube on 2006-05-02
and another comment:
there is a part that is very dapper-specific - namely the double clicking on .deb to get a package installer. that does not exist on breezy. i suggest you put a comment to make it clear that on breezy 5.10, you have to use the commandline method with dpkg -i to install a .deb.

---

### Post by user1397 on 2006-05-03
Bump!

---

### Post by user1397 on 2006-05-03
Sorry, but couldn't resist....BUMP!

---

### Post by nanotube on 2006-05-03
heh
maybe you will have better luck if you start a poll in the ubuntu cafe section...
or at least as a first step, put that link in your sig. ;)

---

### Post by Papa-san on 2006-05-03
OK... So I went to this page, as I was about to start a new thread... LOL

However, when trying to add the repositories, I keep getting the error:

[http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz:) Sub-process gzip returned an error code (1)

I am not entirely sure what this means, but I end up not being able to find 'libtiff3g' which other threads keep telling me is in 'universe' after I refresh the synaptic list...

The 'How-To' has ended up in my bookmarks as well. it is an awesome help!

---

### Post by catlett on 2006-05-03
[QUOTE=nanotube]a comment:
in the part about installing stuff from source
instead of recommending "make install" i suggest that you recommend using "checkinstall". checkinstall is available from the repositories, and what it does is automagically create a .deb file, and install it - that way you can later uninstall with synaptic, without having to rely on "make uninstall", which may not even be present!
and btw, great install guide! i will link to it in my sig, cuz there are always people asking how to install stuff. :)[/QUOTE]
What do you mean by checkinstall? Is it an entirely different process or do you do everything the same except run "checkinstall widget" instead of "make install widget"? It sounds like a totally different process. If so is there a link or wiki about it? (glad to see you're around tonight as well, lots more to learn :-D )


I just ran "sudo apt-get install checkinstall". It also loaded installwatch. Do I need to invoke installwatch when running checkinstall or is it a background app that is monitoring the installs on my system?

---

### Post by nanotube on 2006-05-04
[QUOTE=catlett]What do you mean by checkinstall? Is it an entirely different process or do you do everything the same except run "checkinstall widget" instead of "make install widget"? It sounds like a totally different process. If so is there a link or wiki about it? (glad to see you're around tonight as well, lots more to learn :-D )


I just ran "sudo apt-get install checkinstall". It also loaded installwatch. Do I need to invoke installwatch when running checkinstall or is it a background app that is monitoring the installs on my system?[/QUOTE]

yes, like you say, you just use "checkinstall" instead of "make install" in the process. that's it. :)
i am sure if you search these forums, you will find some more examples of use - but it really is that simple.

---

### Post by user1397 on 2006-05-05
Please make a sticky with  this website: [http://monkeyblog.org/ubuntu/installing.html]("http://monkeyblog.org/ubuntu/installing.html")
because so many new ubuntu users have trouble with this.
you might want to call it:
"New to Linux? Need to know how to install programs?" or a variant ;)

---

### Post by dermotti on 2006-05-05
I always liked that guide...

---

### Post by MetalMusicAddict on 2006-05-05
Dude, you already have a [thread]("http://ubuntuforums.org/showthread.php?t=169596") about this.

---

### Post by PapaWiskas on 2006-05-05
Well I am glad he posted here, because I had no clue about the other post he did.

So thanks erik1397!

---

### Post by MetalMusicAddict on 2006-05-05
He coulda just bumped his old thread. No need to repost threads days (2 to be exact) apart.

---

### Post by BoyOfDestiny on 2006-05-05
No love for  Applications -> add/remove

Granted, the selection isn't as big as synaptic, but I'd recommend it for "common" software to someone who is new to computers. It is just so darn friendly...

P.S. Maybe the mods can merge the two threads?

---

### Post by user1397 on 2006-05-06
[quote=nanotube]a comment:
in the part about installing stuff from source
instead of recommending "make install" i suggest that you recommend using "checkinstall". checkinstall is available from the repositories, and what it does is automagically create a .deb file, and install it - that way you can later uninstall with synaptic, without having to rely on "make uninstall", which may not even be present!
and btw, great install guide! i will link to it in my sig, cuz there are always people asking how to install stuff. :)[/quote]
Good thing he changed it, because now it talks about checkinstall too

---

### Post by user1397 on 2006-05-06
[quote=PapaWiskas]Well I am glad he posted here, because I had no clue about the other post he did.

So thanks erik1397![/quote]
you're welcome!

---

### Post by user1397 on 2006-05-06
[quote=MetalMusicAddict]Dude, you already have a [thread]("http://ubuntuforums.org/showthread.php?t=169596") about this.[/quote]
my bad, i meant to post it somewhere else, i messed up!

---

### Post by user1397 on 2006-05-06
[quote=nanotube]and another comment:
there is a part that is very dapper-specific - namely the double clicking on .deb to get a package installer. that does not exist on breezy. i suggest you put a comment to make it clear that on breezy 5.10, you have to use the commandline method with dpkg -i to install a .deb.[/quote]
Amen

---

