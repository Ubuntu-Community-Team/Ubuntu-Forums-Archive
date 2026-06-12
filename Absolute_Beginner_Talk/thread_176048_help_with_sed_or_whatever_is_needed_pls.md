---
title: "help with sed or whatever is needed pls"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by louis_nichols on 2006-05-14
Hi! I'm not actually an ABSOLUTE beginner (although I'm not very far either :) ), but my question must feel like one, so that's why I'm posting it here.

Here's the thing: I'm trying to get some output about amarok via the dcop interface. Now the unexpected thing about dcop, which is the beginning of this post, is that it can't take more than one argument. So for example I can use
```
dcop amarok player nowPlaying
```but never ```
dcop amarok player nowPlaying album
``` to get both pieces of info about a song.

So I figured I would make 2 commands, like this: ```
myself@home:~$ dcop amarok player nowPlaying && dcop amarok player album
Colours ft. Domino - Hold Me And Kiss Me (Andrea T. Mendoza vs. Steven Tibet Dub Mix)
D I G I T A L L Y - I M P O R T E D - House - silky sexy deep house music direct from New York city!

```The thing is this will print the output on 2 separate lines, and I REALLY need both things to be on one line, separated by a space. So I thought I could use some sed magic, but I can't get it right. I tried ```
dcop amarok player nowPlaying && dcop amarok player album | sed -e 's/\n/ /'
``` which seemed normal to me, but it doesn't do the trick. Can someone help? I know the answer is simple enough, I just can't find it

---

### Post by mostwanted on 2006-05-14
This really hasn't got anything to do with beginner issues. Don't you think the regular support forums or perhaps the programming forum would be a better place to post this?

---

### Post by Jussi Kukkonen on 2006-05-14
How about this:
```
dcop amarok player nowPlaying | tr '\n' ' '; dcop amarok player album
```

---

### Post by louis_nichols on 2006-05-14
[QUOTE=mostwanted]This really hasn't got anything to do with beginner issues. Don't you think the regular support forums or perhaps the programming forum would be a better place to post this?[/QUOTE] I guess you can view it that way. :) I was just trying to be self-ironc. The forums aren't strict about what's being posted where, anyways, and support can be found anywhere.

[QUOTE=Jussi Kukkonen]How about this:
```
dcop amarok player nowPlaying | tr '\n' ' '; dcop amarok player album
```[/QUOTE]

Great, man! Does exactly what I need. Thank you!

---

