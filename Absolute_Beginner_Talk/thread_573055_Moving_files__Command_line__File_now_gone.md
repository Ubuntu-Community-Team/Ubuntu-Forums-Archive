---
title: "Moving files | Command line | File now gone"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by Xarok on 2007-10-11
user@computer:/var/www$ sudo mkdir wp
user@computer:/var/www$ sudo mv index.php /wp
user@computer:/var/www$ cd wp
user@computer:/var/www$ ls

there was no files in the wp directory...
What did I do wrong folks?

---

### Post by skymera on 2007-10-11
ok so you are in /var/www

and you wanted to move the file from where? to /var/www/wp?

perhaps your not in the file directory
example

sudo mb /home/user/Desktop/file /location/of/new/directory

---

### Post by dj Kalma on 2007-10-11
I'd hazard a guess that you now have a directory called wp in your root. 

You had this:
```
user@computer:/var/www$ sudo mv index.php /wp
```
Compare it with this:
```
user@computer:/var/www$ sudo mv index.php wp
```
See the difference? Try this:
```
user@computer:/var/www$ cd /wp
user@computer:/wp$ ls
```

---

### Post by Xarok on 2007-10-11
That's what I guessed at first too...
but it turned out that it changed the filename to wp
and moved it too directory /

I should have done... 
```
sudo mv index.php wp/
```

I think ```
$ sudo mv index.php wp 
```would just change the file's name to wp

Thanks guys

---

### Post by dj Kalma on 2007-10-11
Oh snap, you're right. I was a bit off with my guessing, but at least the general direction was correct.

---

### Post by skymera on 2007-10-11
and i was way off :lol:

---

### Post by Xarok on 2007-10-11
> **dj Kalma said:**
> Oh snap, you're right. I was a bit off with my guessing, but at least the general direction was correct.

So what do you spin Dj Kalma?

I like Proggressive Trance (my name be Dj Kaimeno)

Kalma & Kaimeno.. spinning live on ENT.fm!! I can see in now! lol


Oh, snap your from Helsinki? The home of Linus! 
I was there this summer visiting relatives.

---

### Post by dj Kalma on 2007-10-11
> **Xarok said:**
> So what do you spin Dj Kalma?

I like Proggressive Trance (my name be Dj Kaimeno)

Kalma & Kaimeno.. spinning live on ENT.fm!! I can see in now! lol


Oh, snap your from Helsinki? The home of Linus! 
I was there this summer visiting relatives.

Heh, I proclaim to be the world's only Black Metal DJ. "Kalma" could be translated as "Death", "Corpse" or something appropriately gruesome. So it's a bit no-go with a duet, although I can see the various possibilities in such an attempt.

And yes, metal in all its various forms is the only acceptable type of music in Hell-sinki. I'm quite sure Linus himself is a metalhead.

---

### Post by Xarok on 2007-10-11
> **dj Kalma said:**
> Heh, I proclaim to be the world's only Black Metal DJ. "Kalma" could be translated as "Death", "Corpse" or something appropriately gruesome. So it's a bit no-go with a duet, although I can see the various possibilities in such an attempt.

And yes, metal in all its various forms is the only acceptable type of music in Hell-sinki. I'm quite sure Linus himself is a metalhead.

lol, Linus listening to metal... lol

oh well...

Kalma is a cool name for a Trance Dj I thinks thought.
sounds like a good Goa-Trance name.

The clubs I went to in Helsinki played Trance, DnB, etc. >_>

---

