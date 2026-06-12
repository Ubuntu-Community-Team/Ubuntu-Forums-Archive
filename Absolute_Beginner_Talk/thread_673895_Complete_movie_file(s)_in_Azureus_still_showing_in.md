---
title: "Complete movie file(s) in Azureus still showing in chunks"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by l_ballbag on 2008-01-21
Hi, something weird I found happened using Azureus for the first time after switching back over to Ubuntu from WinXP (currently using GG ver7.10) about a week ago since this very post. I installed Azureus via Synatpec and downloaded a couple of movie files. They appear to have completed as I noted they were in the bottom half window, and no longer in the top.

When I went to play the files, assuming they were avi or mpg, upon opening the folders I discovered that there were still a whole heap of chunked files with extension .r00 (r-zero-zero) right through to .r48 and same on the other file... as if the download was still incomplete...

Can anyone help? I really want to watch these video files!

Thanks in advance.

---

### Post by frup on 2008-01-21
hmm I saw something else like this about a movie earlier which I thought was just a split file.

can you open terminal and cd to the directory of the movie and then type

> cat nameoffiles.r* > movie.rar 

change name of files to the name they share in common. I'm guessing it is a rar file... I may be wrong but see if it works and report.

---

### Post by hyper_ch on 2008-01-21
just unrar them.... first you have to install unrar... then you can click any of those files and have it extracted.

---

### Post by aeiah on 2008-01-21
they're just split archives. scene releases tend to be split into 14mb chunks to aid the initial distribution process before they get put on to bit torrent networks. (they start ther life on ftp, irc and usenet)

although once having a rar application installed will mean you can click on any of them to unrar all of them, it is good practice to open the first one, as sometimes subtitle files or .cue files are only present in archive .rar, .001, .002 for example.

---

### Post by l_ballbag on 2008-01-21
Ah yeh, unrar - of course - one of a couple of apps I forgot to install - thanks all for the advice and quick replies! I think I've seen that cat method to merge 2 separate video files so will look more into that.

Thanks again all.

---

