---
title: "Previewing images before download."
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by Adjutant on 2006-06-28
Hello Ubuntu friends.

I'm having some problems browsing my favorite website. Whenever I want to upload an image, it let's me browse which image I want to upload. Which is what's supposed to happen.

My problem here is that I am not able to view the image I want to upload! ](*,)  

As you can see from the attached screenshot, uploading from a large quantity of images which names are only in random numbers can prove a quite daunting task.

So my question here is, is there a way to change it so that I may preview the image before I upload it? It's a real pain having to open my image folder and memorize the big number then search for that number to upload it and hopefully have not messed up and uploaded the wrong image by accident.

Thanks.

---

### Post by kzutter on 2006-06-28
The problem here is not Ubuntu, but rather a Firefox issue.
Firefox uses its own file dialog instead of using Gnome's or KDE's.
You solution will be to use a web browser that uses the systems file dialogs.
I use KDE, so in this case Konqueror would be my pick for web browser.
It looks like you are using Gnome, I don't use Gnome, so I am not sure, but I think Gnome's native browser is called Galeon - give Konqueror or Galeon a try.

---

### Post by Adjutant on 2006-06-28
thanks!

Damn you firefox :(

---

### Post by aysiu on 2006-06-28
[QUOTE=kzutter]The problem here is not Ubuntu, but rather a Firefox issue.
Firefox uses its own file dialog instead of using Gnome's or KDE's.
You solution will be to use a web browser that uses the systems file dialogs.
I use KDE, so in this case Konqueror would be my pick for web browser.
It looks like you are using Gnome, I don't use Gnome, so I am not sure, but I think Gnome's native browser is called Galeon - give Konqueror or Galeon a try.[/QUOTE]
Really? It appears to me that it's using Gnome's dialogue, not its own. I get the same useless upload dialogue in Epiphany as well.

---

### Post by Adjutant on 2006-06-28
Hmm, that's right, I just checked Epiphany. :(

So it's a GNOME problem? No fix?

---

### Post by aysiu on 2006-06-28
[QUOTE=Adjutant]Hmm, that's right, I just checked Epiphany. :(

So it's a GNOME problem? No fix?[/QUOTE]
None that I know of, apart from using Konqueror.

The annoying thing is that this happens even if you're using Firefox or Epiphany *in* KDE. They still use the Gnome dialogues.

P.S. [You're not alone](http://mail.gnome.org/archives/nautilus-list/2006-March/msg00113.html).

---

### Post by Adjutant on 2006-06-28
I fixed my problem!

Whenever you're browsing images, click on the roller on your mouse! Then preview area pops out.

Edit! Damn, it's not working for me, what did I do to get that preview? I thought it was clicking on the roler thing... hmmm

Second Edit: okay, i've got it now. Apparently the middle-click deal works with Galeon, but not with my firefox, what a shame...

---

### Post by aysiu on 2006-06-28
I tried right-clicking and middle-clicking and scrolling just about anything I could in that dialogue...

I haven't actually tried this, but you may find [this HowTo](http://www.ubuntuforums.org/showthread.php?t=110353) helpful. It's for 5.10, but I'm sure it'd work for 6.06, too.

**Edit**: Never mind. I just tried it. It does integrate Firefox with KDE, but it doesn't use the Konqueror upload dialogue.

---

### Post by Adjutant on 2006-06-28
oh yeah, this is what the preview is supposed to look like.

im going to try that integration thing, i'm sure it'll work

---

### Post by aysiu on 2006-06-28
[QUOTE=Adjutant]oh yeah, this is what the preview is supposed to look like.[/QUOTE]
Yeah, I've seen that dialogue for certain things in Gnome, but apparently it doesn't show up for web browsers...?

---

### Post by Adjutant on 2006-06-28
[QUOTE=aysiu]Yeah, I've seen that dialogue for certain things in Gnome, but apparently it doesn't show up for web browsers...?[/QUOTE]


Well, it works with Galeon web browser, but not Firefox...

And that firefox integration didn't fix the problem, unfortunately.

---

### Post by aysiu on 2006-06-28
[QUOTE=Adjutant]Well, it works with Galeon web browser, but not Firefox...[/quote] That's weird, because Epiphany is supposed to be native to Gnome, but it doesn't work in Epiphany...?

> 
And that firefox integration didn't fix the problem, unfortunately. Yeah, I found that out myself, too.

I think the answer is simple but annoying--find the file in a web browser and remember the name of it. Then upload.

---

### Post by Adjutant on 2006-06-28
Well Galeon is doing something that Firefox isn't. If only we knew what that was and how to fix it...

---

