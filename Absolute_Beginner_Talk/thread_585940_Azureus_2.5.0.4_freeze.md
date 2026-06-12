---
title: "Azureus 2.5.0.4 freeze"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by Ondkloss on 2007-10-21
Hi. So far I've tackled Ubuntu (7.1) pretty well... 
Anyways, I need to use Azureus version 2.5.0.4 becouse the newest versions (like the one used in Synaptic) are flawed in some ways, and I prefer the 2.5.0.4.

But, problem is, I'm not that familiar with manual installation in Ubuntu. I figured Azureus needed no packages or anything, so I downloaded it and unpacked it. Created a launcher and got it running.

It works just perfect until I open a torrent and add a torrent to be downloaded, or simply open a torrent-file using Azureus. Both times it freezes and I've had to kill it (also unable to re-open, I guess some of it's processes are still grinding or something...?)

Quick questions:
- Any pointers to what this could be? Connection configuration?
- I've manually installed Java JDK6 as well, but it works perf with Eclipse and launches Azureus properly. Could this cause any trubble?
- Is there some way when it freezes I can get a report on the state it froze in?

---

### Post by SilverTab on 2007-10-21
Can't help you, but I'm having the *exact* same problem.... both with synaptic's version of JRE and the one I installed myself.... same azureus version!

---

### Post by javeer on 2007-10-21
could you open Azureus using command&#65311; then it should print out some error message.

---

### Post by caecus314 on 2007-11-10
I'm actually having the same problem, too.  I tried running it from the command line, but there doesn't seem to be any activity in the terminal when the freeze occurs.  Hmm...

---

### Post by M-Theory on 2007-11-13
I also have this problem.

---

### Post by Znort_Ubern00b on 2007-11-13
If you are only using it for torretns then i suggest ktorrent. its much more user friendly, i had similar problems with azureus, mine wouldn't even open, would start as if it was then nothing.

install ktorrent through synaptic.

---

### Post by caecus314 on 2007-11-13
Yeah... if I were just using it for simple torrents, I could use Deluge, which has a much cleaner interface and is far more efficient in terms of system resources.  Unfortunately, my university has recently started some questionable practices such as blocking students from downloading anything with a .torrent extension.  If I were using Azureus, I could at least still open magnet URI links.

---

### Post by Tickle Me Elmo on 2007-11-13
I'm seeing similar issues too. When a torrent is added, Azureus crashes down.

---

### Post by microft on 2008-03-07
I'm having the same problem, and as far as I can tell there's nothing related showing up in the output.



```
Starting Azureus...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.7.0]
Configuring environment...
Loading Azureus:
java -Xms16m -Xmx128m -cp "/home/microft/azureus/Azureus2.jar:/home/microft/azureus/swt.jar" -Djava.library.path="/home/microft/azureus" -Dazureus.install.path="/home/microft/azureus" org.gudy.azureus2.ui.swt.Main ''
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'

(SWT:14986): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width 250 and height -1
[plug] [CoreUpdater] Failed to read primary mirror list
DEBUG::Sat Mar 08 00:13:06 WET 2008::org.gudy.azureus2.update.CoreUpdateChecker::getPrimaryDownloaders::504:
  org.gudy.azureus2.plugins.utils.resourcedownloader.ResourceDownloaderException: Error on connect for 'http://prdownloads.sourceforge.net:80/azureus/Azureus3.0.5.0.jar.torrent?download': 403 Forbidden
        at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl.download(ResourceDownloaderURLImpl.java:486)
        at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl$2.runSupport(ResourceDownloaderURLImpl.java:344)
        at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:69)

azureus/azureus: line 112: 14986 Killed                  ${JAVA_PROGRAM_DIR}java -Xms16m -Xmx128m -cp "${CLASSPATH}" -Djava.library.path="${PROGRAM_DIR}" -Dazureus.install.path="${PROGRAM_DIR}" org.gudy.azureus2.ui.swt.Main "$@"
Azureus TERMINATED.

```

---

