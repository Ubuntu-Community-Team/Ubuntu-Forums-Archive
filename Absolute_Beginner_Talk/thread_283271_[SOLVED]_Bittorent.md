---
title: "[SOLVED] Bittorent"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by Cariboo1938 on 2006-10-23
Hi all,
Why is it recommended, actually asked for  [here]("http://www.ubuntu.com/news/EdgyBeta?highlight=%28Edgy%29%7C%28Eft%29%7C%28Download%29") to use Bittorent for downloads? 
I normally use FDM (Free Download Manager) which is very versatile and works perfect.
Thanks for replies in advance.

---

### Post by Synikk on 2006-10-24
> **Cariboo1938 said:**
> Hi all,
Why is it recommended, actually asked for  [here]("http://www.ubuntu.com/news/EdgyBeta?highlight=%28Edgy%29%7C%28Eft%29%7C%28Download%29") to use Bittorent for downloads? 
I normally use FDM (Free Download Manager) which is very versatile and works perfect.
Thanks for replies in advance.

Using Bittorrent to download is recommended because it saves bandwidth for the people who originally host the files on their servers. When you use Bittorrent, the load gets distributed over all of the people seeding/leeching the file. It's generally fast and efficient, and saves people money.

If you can't use Bittorrent, or don't know how, then you can definitely use the FTP/HTTP links to the ISOs and such. If you don't know how to use Bittorrent, there are many tutorials around the net to learn from.

---

### Post by Cariboo1938 on 2006-10-24
> **Synikk said:**
> If you don't know how to use Bittorrent, there are many tutorials around the net to learn from.Thanks Synikk,
I started google-ing and have one more question. I found this and now  I don't what client I should choose:
> Search Google and Download a Popular Bittorent client. Here are some user favorites: BitComet, Azureus, BiTtornado, or uTorrent. Only one is necessary. 
BTW I have a very slow Dial-up connection. Does this matter?

---

### Post by Mission 10 on 2006-10-24
> **Cariboo1938 said:**
> 
BTW I have a very slow Dial-up connection. Does this matter?

Just in the speed of your download. 

I like utorrent, but all of those options are good.

---

### Post by Synikk on 2006-10-24
> **Cariboo1938 said:**
> Thanks Synikk,
I started google-ing and have one more question. I found this and now  I don't what client I should choose:

BTW I have a very slow Dial-up connection. Does this matter?

On Windows, I would recommend [uTorrent]("http://www.utorrent.com/"). On Ubuntu, [Deluge]("http://zachtib.googlepages.com/deluge") is shaping up to be a very nice uTorrent-like client.

Also, downloading on dialup is horribly slow, as you know, I'm sure (I still use dialup sometimes). Downloading through Bittorrent on dialup will be slow as well, but it won't stop you from using Bittorrent entirely.

---

### Post by _duncan_ on 2006-10-24
I always get slower download speed using torrent programs compared to direct downloads. This applies to both WinXP and linux.

A 1.0-1.5 KBytes/sec difference in speed makes a world of difference for a dial-up user, so I always use direct download for large files (anything greater than 20MB).

I also have bad experiences with corrupt downloads using torrent, something I almost never encounter using direct downloads. Maybe it's just my inexperience using torrent programs.

---

### Post by Cariboo1938 on 2006-10-24
> **_duncan_ said:**
>  ......
I also have bad [COLOR="Red"]experiences with corrupt downloads [/COLOR]using torrent, something I almost never encounter using direct downloads. Maybe it's just my inexperience using torrent programs.Interesting comment....Has somebody else the same experience...?

---

### Post by jdong on 2006-10-24
Torrents should actually be more resilient to corruption, as each piece of the torrent is verified against a cryptographically secure SHA1 checksum before being saved. Torrents also pause/resume a lot more reliably than other download mechanisms.

The basic reason why it is encouraged to use torrents is to prevent heavy demand from bringing a download mirror offline... torrents actually excel when there's more people trying to download it.


As far as recommended clients.... Ubuntu comes with a client (gnome-btdownload) that is automatically used when you click on a torrent link. This client does just fine for most torrent downloads. If you are new to torrenting, this is a good place to start.


As you do more torrenting, you may want more features in your torrent client, such as scheduled downloads, or a cool 3D visualization of what's going on. In this case, you can try one of the other torrent clients.

Azureus is arguably the most feature-filled Linux torrent client, but it requires you to have a Java environment, and it's somewhat notorious for using a lot of RAM than what seems necessary (modern versions use around 100-200MB for typical torrenting loads, but it can get drastically worse if you tune the options incorrectly)

KTorrent (yes, ktorrent) is becoming my personal favorite. It's quite feature-complete and nowadays provides very respectable performance for its comparatively low RAM consumption. I know it's a KDE app, but I run it inside GNOME all the time, and it's much lighter than Azureus when considering disk space, memory, and CPU usage, so don't even try that argument :D

uTorrent seems to be gaining sweeping popularity as a lightweight yet great performing torrent client, but it is a Windows-only program. However, it runs well on top of WINE. I personally see this as silly to use uTorrent inside Wine, but it seems like quite some people are doing it nowadays, YMMV. Personally I'd try one of the other options before settling on this.

Finally, Deluge is a relatively new one. I'm not sure what usability status it's in (alpha? beta?) but shows great promise of being a light-weight GNOME-native client.

---

### Post by Cariboo1938 on 2006-10-24
> **jdong said:**
> Torrents should actually be more resilient to corruption,....  :D Thank you, jdong, for the detailed explanations. Right now I'm in transition because I wrecked my Ubuntu 6.06 installation and I'm running Windows XP only and want to prepare the download of the final Ubuntu 6.10 (I learned there are no CDs available for this release, right?).
I'm new to "torrenting" and I first have to get familiar whith the terminology and how it works.

PS.: Sorry, I mis-spelled Bittorrent in the thread title!

---

### Post by jimrz on 2006-10-24
> **Cariboo1938 said:**
> Interesting comment....Has somebody else the same experience...?

strange...i have exactly the opposite experience...never a problem with torrent d/l'd files but have had a few issues with direct downloads. i use Bitorrent and Bittornado about equally. since both perform hash checks before declaring the d/l complete, i seems to make sense that there would be fewer bad d/l's. i recommend the torrent route. also, when you burn the iso to cd do so at the lowest speed your drive will go. this, also, helps reduce errors on the actual cd you will be using.

---

### Post by _duncan_ on 2006-10-24
The torrent program giving me corrupt downloads is Azureus. I'll give the other programs a try.

Thank you jdong and jimrz for sharing your knowledge!

---

### Post by tzulberti on 2006-10-25
I use bttornado, and whenever it downloads something corrupt, the hash take notice, and download it again.

---

### Post by Cariboo1938 on 2006-10-26
> **Synikk said:**
> Also, downloading on dialup is horribly slow, as you know, I'm sure (I still use dialup sometimes). Downloading through Bittorrent on dialup will be slow as well, but it won't stop you from using Bittorrent entirely.Hi Synikk!
You are so right...horribly slow...in my case I think it doesn't make sense. Using uTorrent in Windows XP, with 16 of 17 seeds connected, I get an average download speed of 0.5 kB/sec, which means, it takes 2 weeks and 6 days to get the download done! (Therefore I tried FDM and got 4kB/sec, nearly 10x faster)

---

### Post by jdong on 2006-10-26
If you're on dialup just use the regular mirrors.... :)

---

### Post by Cariboo1938 on 2008-01-05
> **jdong said:**
> If you're on dialup just use the regular mirrors.... :)
Now I use ktorrent with an average DL speed of 2.5 kb/s.
It's awfully slow, but I have the patience and the time.
BTW.: It is astonishing, there was never any corrupted download, even if it took days to dl.

---

### Post by rubicon on 2008-01-05
Well, one of my first posts on these forums was [http://ubuntuforums.org/showthread.php?t=599174](http://ubuntuforums.org/showthread.php?t=599174)

Briefly, I had downloaded dvd image of Gutsy Gibbon and it was corrupt. Torrents have helped me to recover A LOT of data without much pain. Thanks to hash data in .torrent file, which is used to test integrity of a file part-by-part.

---

