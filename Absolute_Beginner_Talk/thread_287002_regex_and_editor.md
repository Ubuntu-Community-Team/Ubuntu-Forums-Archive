---
title: "regex and editor"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by helphope on 2006-10-28
Hi.
I was wondering which program I can choose inorder to use regular expressions; I'm in doubt between vim or emacs.:-k 
In any case any other suggestion is welcome.

Thanks

---

### Post by AgenT on 2006-10-28
vim and emacs are text editors (okay, so emacs in an operating system minus the kernel ;)) and both accept the use of regular expressions in manipulating files and text. However, the "real" regex programs are sed and awk. sed is more of a one-liner type program and very useful at the command line (bash) where awk is more of a scripting language. sed is where you should start and is more regex-like. Then try awk which is very useful too.

Just type sed into your favorite internet search engine and you will get a lot of results. Also try "sed tutorial" and so on.

---

### Post by bsussman on 2006-10-28
Both will use regex but it takes a very special insanity to use emacs ;)

Emacs users will disagree, of course, but they are wrong :mrgreen:

Please note that different programs have subtly different regex implementations.

You need to match the tool to the task - even grep can use regexes, but you cannot edit with it...  The original unix philosophy was 'many sharp tools' meaning small programs that did something narrowly defined, very well.

---

### Post by helphope on 2006-10-28
Thanks a lot. I'll start with sed and then awk. I just asked 'cause I saw I was going to spend a lot of time on emacs and vim.
thanks again

---

### Post by AgenT on 2006-10-28
You should also note that a lot of regular expressions that works in sed will work in vim and also the other way around. Exceptions being few, with command line arguments being the major difference.

Also note that vim is an editor and is very small - but VERY powerful. Because of this it is very portable and included in almost every distribution by default (especially ones that are geared toward advanced users or servers). Good thing to learn if you are a system administrator or work on computers that do not belong to you.

And yes, you actually have to learn to use vim (same for emacs). Vim looks much more intimidating at first because of using different modes (visual, editing, etc.). But once you are used to switching between visual and editing (use "i" to enter editing under your cursor, "ctrl+c" to exit editing into visual), you will see how amazing it is that these modes exist and how much faster everything works. Yes, it does improve how fast you edit files, even though at first that seems backwards. 

For some random tutorials, see:
[http://www.apmaths.uwo.ca/~xli/vim/vim_tutorial.html]("http://www.apmaths.uwo.ca/%7Exli/vim/vim_tutorial.html")
[http://www.unb.ca/documentation/UNIX/tips/vim/](http://www.unb.ca/documentation/UNIX/tips/vim/)
[http://www.vi-improved.org/tutorial.php](http://www.vi-improved.org/tutorial.php)

Here is a good starting point AFTER you learn to USE vim:
[http://www.rayninfo.co.uk/vimtips.html](http://www.rayninfo.co.uk/vimtips.html)

ATTACHMENTS: Attached are a few files that are useful for vim and regular expressions. They are handy "cheat sheets".

---

### Post by helphope on 2006-10-29
Thanks AgenT,
I've already tried out the first tutorial you wrote down on your list. So far quite easy and progressive.
I'm not a system administrator, and my need to learn to use an editor with regex is to find words in text files. I mean words which are near to each other, not next to each other.

Regards:)

---

