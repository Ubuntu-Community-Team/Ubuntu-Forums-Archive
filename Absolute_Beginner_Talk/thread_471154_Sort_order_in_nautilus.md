---
title: "Sort order in nautilus"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Patrick K on 2007-06-11
In Windows when I wanted to move a file to the top of file listing in Win Explorer I would put a "[COLOR="Red"]~[/COLOR]" in front of it. This doesn't work in Nautilus. Is there a way to force a file to the top of the file listing?

More generally, how does Linux sort items?

---

### Post by H.E. Pennypacker on 2007-06-11
> In Windows when I wanted to move a file to the top of file listing in Win Explorer I would put a "~" in front of it. This doesn't work in Nautilus. Is there a way to force a file to the top of the file listing?

Nautilus does exactly what you're describing for me.  Try another symbol if ~ doesn't work.

> More generally, how does Linux sort items?

There's no certain way of doing things across Linux distros.  Nautilus is what controls this. Nautilus will sort by number and alphabet.

---

### Post by Patrick K on 2007-06-11
Thanks for the reply. None of the symbols worked for me. Nautilus still sorts by the first letter of the filename. Putting a number in front does work.

---

### Post by David_1cog on 2007-07-11
This problem is bothering me as well.  

I'm in the process of migrating from Windows, and have many folders and files prefixed with '_' or '!' because I want them at the top of the listing.  Nautilus is ignoring these and all other special characters.

Can anyone suggest a fix?

---

### Post by Nameless_one on 2007-07-11
Why doesn't numbering suffice for you?

---

### Post by David_1cog on 2007-07-11
> **Nameless_one said:**
> Why doesn't numbering suffice for you?

"I'm in the process of migrating from Windows, and have many folders and files prefixed with '_' or '!' ..."

---

### Post by Molerat on 2007-08-22
Bumping because I am having the same problem.  I think it has to do with the locale settings.  Setting LC_COLLATE=C restores the desired sort order for the terminal, but Nautilus does not seem to see the changes.  Anyone have any ideas?

---

### Post by David_1cog on 2007-08-22
It's a known bug in Nautilus:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/131529](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/131529)
[http://bugzilla.gnome.org/show_bug.cgi?id=458707](http://bugzilla.gnome.org/show_bug.cgi?id=458707)

---

### Post by asmoore82 on 2007-08-22
Workaround.. navigate to the folder in a terminal and then run this to add a double number 0 to all those filenames ...

```
~$ for file in [~_\!]*
> do
> mv "$file" "00$file"
> done

```

---

### Post by yossman on 2007-09-03
hey guys, i'm posting what i consider to be a related snafu (bug) in nautilus file sort order.

i name some files with dates at the beginning, like this: 2007-09-03.1.something...'.  this is so they sort in a particular order when sorting by filename, the default sort order.  now when you add a zero(pad) to the beginning of what i am using as an 'index digit' part of the filename (1 -> 01), nautilus continues to sort it exactly the same, even though, that's not 'correct', not only because sorting by name means NAME, not NUMBER (STRING vs INT), but also, that's the way it works on almost all other file managers i've ever used on any operating system for the last 20 years, which is no small amount of history in the computer world.

here's an illustration/example of this messed-up 'sort by name' situation in nautilus.  this is when sorting by 'name' column, in list mode, ubuntu 7.04:

```

2007-09-03.01.filename.jpg
2007-09-03.1.filename.jpg
2007-09-03.02.filename.jpg
2007-09-03.2.filename.jpg

```

**that's just wrong.  it should sort like this:**

```

2007-09-03.01.filename.jpg
2007-09-03.02.filename.jpg
2007-09-03.1.filename.jpg
2007-09-03.2.filename.jpg

```

it has been pointed out to me by some friends that when you're sorting music files, for example, the 'forget about zero-padded numbers in names' is useful for getting the files to sort right for track numbers, BUT, this does not change the fact that the behaviour is a 'smartness' added to nautilus that is basically just 'wrong' to put in there.

if people want their filenames to sort correctly, they can zero pad the numbers themselves, or, get their production software to automatically do it when renaming something.  you don't get the file manager to 'automatically' do it for them, or you screw up everyone else who just wants files to sort the way they do when sorted by name, on almost every other computer platform in use today on this planet.

when i use windows explorer, when i use 'ls' in a unix shell (tcsh/bash whatever), they all sort the second way, not the way nautilus does it.   if you want acceptance on the desktop one of the things you have to keep working at is consistency with things like file name sorting, ESPECIALLY when there are so many traditional file managers out there that do it one way, and then you decide to do it another way.

if this was a configurable option (OBVIOUS configuration option, not something buried in some 'registry-lookalike' somewhere like gconf), that would also be acceptable, with the default method being the old, traditional behaviour for filename sorting.

i couldn't find a matching bug report in launchpad, if someone sees one there could they please attach it to this thread so we can track that too.  if there isn't a bug report filed yet, i can do it, but i'm finding it pretty hard to believe no one else has run into this yet and hasn't filed a bug report already.

thanks for reading, ttys.

---

### Post by Molerat on 2007-09-05
^ I think that's the same "bug."  Meaning Nautilus ignores special characters by default.  In any case, Nautilus actually DOES respect LC_COLLATE settings.  The trick is to put **export LC_COLLATE=C** into your .bashrc file and restart Gnome.  Apparently Nautilus only checks the locale setting at startup.

EDIT:  Actually no, this doesn't work afterall; nevermind.

---

### Post by David_1cog on 2007-09-11
After an unpleasant exchange with some of the Nautilus devs at [http://bugzilla.gnome.org/show_bug.cgi?id=458707](http://bugzilla.gnome.org/show_bug.cgi?id=458707), the 'bug' has been closed as 'Not A Bug'.  It is entirely to do with the locale, as Molerat said.

I don't have access to Ubuntu at the moment (and won't until I build a new system in the coming weeks), so can't test myself.

I found [http://blog.andrewbeacock.com/2007/01/how-to-change-your-default-locale-on.html](http://blog.andrewbeacock.com/2007/01/how-to-change-your-default-locale-on.html) for changing locale.  If this provides a fix for anyone, please report back here so we'll all know what to do.

---

### Post by Molerat on 2007-09-12
> **David_1cog said:**
> After an unpleasant exchange with some of the Nautilus devs at [http://bugzilla.gnome.org/show_bug.cgi?id=458707](http://bugzilla.gnome.org/show_bug.cgi?id=458707), the 'bug' has been closed as 'Not A Bug'.  It is entirely to do with the locale, as Molerat said.

I don't have access to Ubuntu at the moment (and won't until I build a new system in the coming weeks), so can't test myself.

I found [http://blog.andrewbeacock.com/2007/01/how-to-change-your-default-locale-on.html](http://blog.andrewbeacock.com/2007/01/how-to-change-your-default-locale-on.html) for changing locale.  If this provides a fix for anyone, please report back here so we'll all know what to do.

I saw that.  At first I thought that it WAS a bug because I put the locale setting in .bashrc, but Nautilus did not respect it.  On further inspection, it seems that .bashrc is for interactive shell-based stuff only, so it makes sense that Nautilus wouldn't read its settings.  It DOES, however, work if you put **export LC_COLLATE=C** into .gnomerc and restart.  There's probably a more proper place for this setting (wherever system-wide user settings should go), but .gnomerc does the trick.

EDIT:  Note that this will tell Nautilus to use ASCII sort order.  Meaning files will be ordered first by (most) special characters, then uppercase characters, then lowercase characters.  This is, I believe, the old school Unix way of doing things, but it is NOT the Windows way of doing things.  Windows sorts by special characters, then by normal characters, case-insensitive.  ASCII sort takes case into account.  Personally that's what I prefer, but it may not be what other people are expecting.

---

### Post by David_1cog on 2007-09-13
> **Molerat said:**
> ... LC_COLLATE=C ... will tell Nautilus to use ASCII sort order.  ...  ASCII sort takes case into account.  Personally that's what I prefer, but it may not be what other people are expecting.

Thanks for the update - that's definitely an improvement on the current sort method (whatever arbitrary method that happens to be!).

However, I'd prefer the 'Windows' method, because that's what I'm used to and see no benefit in the 'pure ASCII' method (unless someone can point out a benefit?).

Any suggestions on which locale to use to achieve that - or where to go to find out?

TIA.

---

### Post by David_1cog on 2007-09-13
For those wanting to do a bit more reading on this topic, I found the following two articles useful:

[http://www.iac.es/sieinvens/siepedia/pmwiki.php?n=Tutorials.LinuxLocale](http://www.iac.es/sieinvens/siepedia/pmwiki.php?n=Tutorials.LinuxLocale)
[http://www.linux.com/articles/53781](http://www.linux.com/articles/53781)

I've not yet found anything that tells me what sort method each LC_COLLATE does.

Also, can anyone suggest where we go to discuss / request that the default Ubuntu behaviour be changed - the current setting seems illogical to me (i.e. ignoring special characters).

---

### Post by Guy Gizmo on 2008-04-03
Bumping because I'm interested in whether this has been solved.  I'd also like Nautilus to sort in the same order as Windows, if possible, because I'm connecting to a lot of windows file servers where the file names have been very intentionally named to be sorted in a certain way,  (This means that I can't change the file names to change the sort order.)

Has anyone found a solution for this?

---

### Post by bkraptor on 2008-04-18
Been waiting for a solution to this problem too. I've been using Ubuntu on my laptop for overa year now and this is one of the major things that annoy me. The other is that nautilus can't compare to Total Commander and there's no proper replacement for it (where you can do everything with keyboard only, and just as fast).

---

