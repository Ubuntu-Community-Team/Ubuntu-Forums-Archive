---
title: "What does kfmclient do?"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by ofb on 2008-01-17
I'm experimenting to see if there's any way to get Konqueror to launch faster. Often it takes longer than Gimp.

I notice my menu item runs the command 'kfmclient openProfile webbrowsing'. If I run 'konqueror' in terminal instead, there is no difference. The same Konq launches, and alas just as slowly.

So, why is kfmclient used? Is it simply a way to pass options like openProfile? Can't you do that with something like 'konqueror openProfile webbrowsing'?

----

And if anyone does know how to speed up Konqueror, that would be wonderful. It's my favorite file manager, but oh my good gosh it's slow.

Nautilus isn't much faster I might add. Why is that? While the overall performance of Linux on this machine is much better than under Windows, I really miss the relatively instant file manager that Explorer was.

---

### Post by PeterJS on 2008-01-17
Everything you ever wanted to know and more about kfm and konq:
[http://developer.kde.org/documentation/other/kfmclient.html](http://developer.kde.org/documentation/other/kfmclient.html)

I think the slow down might be related to caching. Explore is so tightly bound in to windows that even when "closed" it doesn't unload from memory, where as Konqueror does. Running in a full gnome desktop nautils should open nearly instantly as it is also kept open, as it's nautils that managers the gnome desktop, like explorer does in windows.

---

### Post by ofb on 2008-01-17
I did see and read that, thanks. What I couldn't figure out is why kfmclient is used instead of just adding options to a 'konqueror' command. Especially since you can launch konq with 'konqueror'.

So I guess what I'm asking isn't 'What does kfmclient do?', but 'why is kfmclient used?'

About the slowness -- so, essentially a full-figured file manager like Konq is just going to be slow to launch unless it's pre-launched by intergration? And it's not intergrated to free up resources for speed when you're not using it?

Guess that would make some sense. Still I wish when it was loaded it would be instant when you click something. There's usually a half or full second pause before it goes to where you asked it. Nautilus is slighly better, but neither is instant like Explorer.

---

