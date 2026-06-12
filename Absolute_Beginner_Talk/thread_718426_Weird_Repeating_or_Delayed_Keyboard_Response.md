---
title: "Weird Repeating or Delayed Keyboard Response"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by Andavane on 2008-03-08
Hello

In Ubuntu 7.10 Gutsy my keyboard response has gone most peculiar.

When I type, there is either a delay between striking the key and the letter appearing onscreen or (much more commonly) when I strike a key, the letter repeats itself. It is so bad in Ubuntu as to be unusable now: the only way I can eventually type is to strike each key very lightly indeed. Then there is a chance.

I first noticed the problem this morning, when coming out of suspend*. When I typed in my password it rejected it. I tried again and again, not knowing what the matter was.

Rebooting did not help. 

I rebooted into Windows XP, and keyboard is fine in every respect, so I know the problem is not the keyboard. I am of necessity having now to post this in Windows.

Any ideas?

Regards

John

PS: I do think it is a good idea for new (and perhaps not-so-new) linux users to have an alternative operating system to boot into, in order to be able to eliminate, say, the keyboard in this issue. I first thought that perhaps the keyboard was simply beginning to wear out.

* On a similar case a few days ago, a similar thing happened when coming out of suspend. This was fixed after rebooting. 

a response:
[http://ubuntuforums.org/showthread.php?t=309366](http://ubuntuforums.org/showthread.php?t=309366)

Would it help to post the contents of the xorg.conf file?
I have investigated as far as I am able, and now need some help.

---

### Post by one_iota on 2008-03-08
I've no idea if [this]("http://tldp.org/HOWTO/Keyboard-and-Console-HOWTO-17.html") short article is of any relevance in your case? It starts by saying: "*At startup, the Linux kernel sets the repeat rate to its maximal value. For most keyboards this is reasonable, but for some it means that you can hardly touch a key without getting three copies of the corresponding symbol*."

---

### Post by Andavane on 2008-03-09
Thank you, one_iota.  It certainly seems to be in that area.
After writing this I had lunch and then rest.
When I turned the PC on, the problem had entirely disappeared.
So we can just see whether it happens again, or whether it was just one of those strange things.
Kind regards
John

---

### Post by Andavane on 2008-03-10
Hello
Since making this post, I put the stem into hibernate, and when I came out of hibernate, the same phenomenon happened again (yesterday it was after coming out of suspend).
So although I could use suspend and hibernate earlier, it seems that now I have to completely avoid these options.

The situation was resolved by boting into Windows XP and working on that, then shutting down the PC and starting into Ubuntu again some time afterwards.

Regards

John

---

