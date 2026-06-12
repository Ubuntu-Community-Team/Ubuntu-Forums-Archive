---
title: "Another Evolution crash - after general Synaptic update"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by stig on 2006-05-30
About 40 minutes ago someone else reported an Evolution crash. Now I have one, but slightly different. I've searched the Ubuntu forum pages and on Google but cannot find a reason or a solution. Perhaps I need to re-install Evolution but I want to check to ensure I don't lose any mail. The problem is as follows.

I booted up the PC, opened Evolution and clicked send/receive. Then I started Gftp and sent a couple of files to my web site. Meanwhile, the automatic update told me there were updates to download so I clicked to start that.

The log for that update was:
Commit Log for Mon May 29 14:20:38 2006
Upgraded the following packages:
libpq3 (1:7.4.8-17ubuntu1.1) to 1:7.4.8-17ubuntu1.3
python-pgsql (2.4.0-6ubuntu1) to 2.4.0-6ubuntu1.1
python2.4-pgsql (2.4.0-6ubuntu1) to 2.4.0-6ubuntu1.1

The update went OK. I closed Gftp and clicked on my first new mail message in Evolution. What I got was a warning: "The application "Evolution" has quit unexpectedly" and the options of Restart Application, Close, or Inform Developers. Restart simply closed Evolution. When I opened Evolution again I got the same warning - and the same result on clicking either Restart or Close.

If I start Evolution in the terminal I get the same result and in terminal it shows:

adding hook target 'source'
(evolution:7685): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed
(evolution:7685): GnomeCanvas-CRITICAL **: gnome_canvas_request_redraw: assertion `GNOME_IS_CANVAS (canvas)' failed
evolution: tif_jpeg.c:1505: JPEGCleanup: Assertion `sp != 0' failed.

If I must re-install Evolution how do I make sure that I keep all my mail? I guess I should copy the .evolution files, but are there any files elsewhere that are needed for the mail and configuration?

This is the first big crash I have had on Ubuntu after months of superb performance. Help would be greatly appreciated!

---

### Post by nudnik on 2006-05-31
Being a Nudnik, I cant be of much help, but I have experienced the same problem after upgrading. I imagine its one of the many bugs they will sort out shortly in the final release of Dapper.

---

