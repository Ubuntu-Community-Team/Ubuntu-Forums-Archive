---
title: "system monitor"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by Baelfael on 2007-06-21
can anyone recommend a system monitor for my GNOME desktop, other than conky, gdesklets, or screenlets? adesklets doesn't work for me either. -_-

---

### Post by Happy_Man on 2007-06-21
Not sure about GNOME (you've just struck down every option I know of), but on KDE there's SuperKaramba.

---

### Post by Crafty Kisses on 2007-06-21
> **Baelfael said:**
> can anyone recommend a system monitor for my GNOME desktop, other than conky, gdesklets, or screenlets? adesklets doesn't work for me either. -_-

Gkrellm works really good:
```
sudo apt-get install gkrellm
```
Hope this helps. :D

---

### Post by John.Michael.Kane on 2007-06-21
What problems are you having with these aforementioned programs? As posted before you pretty much cut down all monitoring programs.

Short of gkrellm which is posted above.

---

### Post by Baelfael on 2007-06-21
1. adesklets: This is one I WANT to use, but it just doesn't work! I install it using the Synaptic Package Manager. And then it does not appear in my Accessories menu like it should, and when I try running it from terminal:
```
adesklets
```
I just get a blank response, and it just goes to my $ directory thing. Like this:
```

robbie@laptop:~$ adesklets
robbie@laptop:~$ 

```
I don't know whats wrong and the adesklets website isn't helping at all.

2. gDesklets: I just hate the desklets they provide. They are buggy, they always crash, it's just crap.

3. Screenlets: Relies on Beryl/Compiz, and those programs slow my computer down. And it doesn't have a wonderful system monitor either.

4. Conky: Conky for me acts as a dead image sitting on my desktop, and when a box overlaps it, it just disappears. And then I did what the website said, 
```
$ zcat /usr/share/doc/conky/examples/conkyrc.sample.gz > ~/.conkyrc
```

And that just messes it up more by putting it in a giant window when run, which takes up half of my desktop and pisses me off.

I want to use aDesklets, so if anyone can help me with that, I'd be grateful.

---

### Post by diatribe on 2007-06-21
when you run adesklets from a prompt it just starts the daemon, you have to find the python file for the desklet and run that after running adesklets.  and what do you mean about conky?

---

### Post by John.Michael.Kane on 2007-06-21
Have you tried this adesklets guide [http://doc.gwos.org/index.php/Adesklets](http://doc.gwos.org/index.php/Adesklets)

Corresponding thread here.[http://ubuntuforums.org/showthread.php?t=183709&highlight=adesklets](http://ubuntuforums.org/showthread.php?t=183709&highlight=adesklets)

---

