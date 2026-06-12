---
title: "[Fix] poor quality of exporting Dia diagrams into .png format"
date: 2008-05-27
forum: Art &amp; Design
---

### Post by mihai.ile on 2008-05-27
If some of you actually try Dia - a simple software for creating diagrams, a visio alternative (a very simplistic one) and after all the work finds that the exported .png file has very low quality this is how to fix it:

It seems that when exporting with Dia if you do:
Under "File->Export..." in the dialog select: "Determine file type: By
extension" and under "Name: " put something like "test.png"
the final .png has poor quality, and no antialiasing is used.

But by doing:
under "File->Export..." in the
dialog select "Determine file type: Portable Network Graphics (*.png)" and
Under  "Name: " put something like "test2.png"
Now a window will ask about image size, just click "ok".
the final .png now is antialiased and the quality is perfect!

I described the bug here with a simple example: [http://bugzilla.gnome.org/show_bug.cgi?id=535179](http://bugzilla.gnome.org/show_bug.cgi?id=535179)

If someone can reproduce this I would appreciate to comment on the bug. Thank you.


I actually lost several hours trying to fix this so I hope this will be useful in saving your time...

---

### Post by TomSharp on 2009-04-08
I can report repeating this in Ubuntu 8.10 with Dia 0.96.1.

Thanks for the information, it is very helpful to me.

---

### Post by anaxagold on 2012-11-11
I can reproduce exactly the same behaviour with Xubuntu 12.10 and Dia 0.97.2

Many thanks. Many hours lost ... and now save thanks to you.

---

### Post by overdrank on 2012-11-11
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

