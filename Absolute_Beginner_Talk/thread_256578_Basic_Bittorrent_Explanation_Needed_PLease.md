---
title: "Basic Bittorrent Explanation Needed PLease"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by 3rr0r on 2006-09-13
Okay, I have googled, wikipedia'd and read everything (well first 3 pages of google), but no specific, straightfoward explanation of how this torrent system works.  

Based on what I have read and my hardware (opera browser, pirate bay, and bittorent) I have gathered the following and wish for confirmation or correction.

I use Opera browser and surf to piratebay.  I search for torrents and it displays them.  

-Basically pirate bay is a large map that tells my system where the torrent I am searching for is.

I click "Download Torrent" and I am prompted that this is initializing a bittorrent download.  I tell it where to save the torrent and bam, a folder is created with all the files (although each file is 0.0 kb when the d/l first starts).  Opera opens a new window showing me the transfer status of the torrent file.  When the download is done, the file size of each song is its appropriate size and I now have music to play.

- Bittorrent is launched through Opera.  Bittorrent is my client that allows the transfer of data to my computer from someone else's or vice versa.  

The part I am really confused at is, besides the folder that is created with the files inside, there is also a file created that is given a .torrent extension.  When I manually choose to run bittorrent, it prompts me for the location of the torrent.  I guide the program, then it prompts me for the associated files (music files that I downloaded) and I do that.  It then scans or does something, then says "Download Sucessful" after it runs through each file quickly.  Also, a red light in the top right corner of the window is on. 

What I do not get is what exactly is happening when I do this with bittorrent?  What is it scanning and telling me the download is done, when I have known that already ?  I am trying to understand the entire bittorrent process, and running the program manually so far has no purpose to me.  Is that what is happening as I download the files, so manually running it, is redundant?  Thank you for any input.

---

### Post by 3rr0r on 2006-09-13
shameless bump

---

### Post by benfindlay on 2006-09-13
Basically, piratebay/torrentspy/isohunt etc etc are sites that contain links to people who are sharing data. The files they supply are the torrent files. The torrent files contain data that allows your pc to link to the people sharing the information and get the data from them. The torrent client (azureus/bitcomet/bit tornado etc etc) allow your computer to access th torrent file and retrieve this data from other people

The file is downloaded over time and a progress bar is shown. The "scanning" you mentioned is done at the end of the download. This is called a "hash check". Your computer checks the data you have against the data the torrent file told it to expect, an, if all is peachy, then the file finishes. If some data is missing, it requests this outstanding data.

It is important not to get confused between the torrent file itself and the files you are trying to get. The torrent file is effectively a glorified map telling you where stuff is. And piratebay can be thought of as a library of hundreds/thousands of these "maps"

Hope this helps

---

### Post by halcyon on 2006-09-13
From what I'm gathering, you're downloading a torrent, it runs, finishes, and then you open your BitTorrent client manually, and are confused to what it's doing when it asks you for the .torrent file and then the files downloaded?

EDIT: benfindlay beat me :(

---

### Post by 3rr0r on 2006-09-13
So, after I download the torrent file, do I need to manually run bittorrent to make sure the data hash is correct?  

I was able to play the music files without running them manually through bittorrent, so do I have to run each torrent through bittorrent manually or ?

---

### Post by halcyon on 2006-09-13
When you run the client manually after downloading the files already like that, all the client does is first check the data to make sure it hasn't been edited or corrupted, and then lets users download pieces from you.

You don't need to run it manually every time after downloading to check the files, they're already checked automatically while you download.

---

### Post by 3rr0r on 2006-09-13
> **halcyon said:**
> When you run the client manually after downloading the files already like that, all the client does is first check the data to make sure it hasn't been edited or corrupted, and then lets users download pieces from you.

You don't need to run it manually every time after downloading to check the files, they're already checked automatically while you download.

awesome, thanks for the info.  That makes a lot of sense now.

---

### Post by halcyon on 2006-09-13
You're weeeeellllcome!

---

