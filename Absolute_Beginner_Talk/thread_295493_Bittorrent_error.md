---
title: "Bittorrent error"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by Zeerak on 2006-11-08
Okay so I installed the bittorrent client you get from just apting bittorrent-gui it installs fine and all of that, but then I try to run a torrent and it gives me the warning:

"Mailcap file /etc/mailcap, line 74: incomplete entry ignored"

So I looked at line 74 in that file and it says:

```
application/x-sc
```

it's also by far the shortest line in the entire file, so I can see why it would seem incomplete to the application, but the thing is, what is to be written in the rest of it?

And also, i'm running edgy

---

### Post by rlozano on 2006-11-08
i suggest you use the KDE torrent application called Ktorrent. u can install it using sunaptic or by issuing the command [PHP]sudo apt-get install ktorrent[/PHP] in the terminal.

hope this helps.

---

### Post by Zeerak on 2006-11-08
I'm using xubuntu though. Would it matter if I use a KDE application for an xfce environment?

---

### Post by Kateikyoushi on 2006-11-08
I would recommend to give rtorrent a try, yes it runs in terminal but on the bright side uses almost no resources and it's very stable and still useable. You can set it up to start torrents automatically etc.

---

### Post by jmikola on 2007-03-04
> **Zeerak said:**
> "Mailcap file /etc/mailcap, line 74: incomplete entry ignored"

So I looked at line 74 in that file and it says:

```
application/x-sc
```

i sorted this out by modifying the mailcap file myself and removing the line-break after the semicolon in "application/x-sc;", but noticed the problem kept coming back periodically. it looked to be a problem with gnumeric itself. since then, i found what looks to be a permanent solution, courtesy of another forum. it points out the gnumeric-specific file to correct.

> I'm using Ubuntu Edgy (6.10). This is how I fix my problem. Thanks you kelpy2k6.

First, edit the gnumeric OR gnumeric-gtk. (depends on which version of gnumeric is installed, the one I'm using is plain gnumeric):

```
sudo gedit /usr/lib/mime/packages/gnumeric
```

Go to the two lines that looks like this:

```
application/x-sc;
gnumeric '%s'; edit=gnumeric '%s'; description="SC/XSpread spreadsheet";
```

Then edit it into one line like this:

```
application/x-sc; gnumeric '%s'; edit=gnumeric '%s'; description="SC/XSpread spreadsheet";
```

Then run:

```
sudo update-mime
```

source: [http://www.talkgraphics.com/showthread.php?p=197320]("http://www.talkgraphics.com/showthread.php?p=197320")

---

