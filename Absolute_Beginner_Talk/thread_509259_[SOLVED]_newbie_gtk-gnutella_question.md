---
title: "[SOLVED] newbie gtk-gnutella question"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2007-07-25
I just installed GTK-Gnutella using Add-Remove...
It's installed, and I was able to download the first (and so far only) thing I looked for.
My problem is: how do I filter the results? So that I don't get any executable files or pornographic material in my search results?
Please help.
Thanks.
P.S.:In case GTKG doesn't provide for such filtering, which P2P client should I opt for? I don't want to use the BitTorrent things because I have no idea how they work, and am not about to explore for a few more days. Being able to set filters to not get pornography  in my search results is a very important criteria for me.

---

### Post by kleo skywalker on 2007-07-25
I know it seems like a small problem, but please help!

---

### Post by kleo skywalker on 2007-07-25
Not a single response in 5 hours?! Please help people, thanks.

---

### Post by cbiere on 2007-07-25
A simple way is to add negative or positive match patterns when you enter your search term.
For example:

whatever -.mov -.wma -.wma -.exe

That will search for anything with "whatever" in the filename but discard all results with .mov, .wma and so on in the results. You can also use positive patterns like this:

some artist some title +.mp3

That will discard all results that don't match .mp3 like ZIP files, executables etc. If you want other filter rules for filtering by size or don't want to type this each time, you can create filters with one or more rules in advance and select it when you submit your search.

Have a look at the manual:
[http://gtk-gnutella.sourceforge.net/manual/](http://gtk-gnutella.sourceforge.net/manual/)

The section about filtering explains filter rules a bit:
[http://gtk-gnutella.sourceforge.net/manual/filtering.html](http://gtk-gnutella.sourceforge.net/manual/filtering.html)

---

### Post by kleo skywalker on 2007-07-26
Thanks.
Looked through the manual. It certainly isn't simple. Moreover, it doesn't seem to give a way to filter for content.
Like in Ares, you can customize your settings so that you don't get any pornographic material in your search results - that is precisely what I want to do. So, how?

---

### Post by cbiere on 2007-07-26
You can only filter by content if you have a database that contains correct information about the file contents. Otherwise you can only use some heuristics by filtering out files which seem to have certain content but this is going to be very error-prone especially if there are people who are mislabeling files on purpose.

What you could do is using [http://bitzi.com/](http://bitzi.com/) and search there. Bitzi gives you access to searchable user-provided meta information about files which have been indexed by their users. If you find something there you'd like to download you can use the magnet-link you'll get and paste or drag&drop that to gtk-gnutella. You might also want to search for the filename or a part thereof because their magnet-links are unfortunately not very reliable as they provide no actual source for these files but only a key to find them. Also their database only indexes a small fraction of the content available on Gnutella. The information is fairly accurate though and most listed content is also of good quality.

That said it's not so difficult to avoid content you're not interested in. Just look at the search results you get. Look at the file types, the filenames, the filesizes. Don't rely on the computer to think for you. Computers are easily fooled, people with just a little bit of experience aren't and the spammers are not horribly smart anyway. Further you can preview files as they are downloaded and abort the download if you realize it's not what you want. Furthermore, once you find good files, you can usually browse the hosts which provide them and find more related content. This reduces the likeliness that you're downloading anything bad by accident.

However, if you believe in word filters, just create a list of "rude" words and use them as filter. As far as I can tell, this is exactly what other software is doing to filter out pornographic stuff. I find it quite ridiculous and stupid. It also causes a good amount of false-positives, but that's up to each user of course.

Just in case you want to download something for your kids: Make sure you preview the files after downloading. If possible only fetch what Bitzi lists as good and safe. Never, ever, let a child use any kind of file-sharing software. The internet is an adult-only zone and that's a good thing.

---

### Post by kleo skywalker on 2007-07-26
Solved [here]("http://ubuntuforums.org/showthread.php?t=510102").

---

