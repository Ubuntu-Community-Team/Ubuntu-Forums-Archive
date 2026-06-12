---
title: "would appreciate some tips on minimising downloading data"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by jasonwatkins on 2007-09-23
to explain a little of what i mean, i got a letter from my ISP two weeks ago saying that in the previous month i'd gone over my 40gb download limit.

it isn't a hard and fast limit mind, but they have halved it for 4 weeks and set a limit of 5gb a week.

the thing is, the month I went over was the first full month I spent on Linux.

I admit, i was adding and removing stuff, apt-get updating, and apt-get upgrading quite a lot as well.

so i'm just wondering if my overall daily usage of linux basically pushed me over the top ??

i don't download a huge amount a month as it is - a couple of tv shows and some music, but it seemed somewhat strange that the first full month I was on Linux, I go over my download limit.

i've just re-installed and re-set up my PC this weekend after not having the internet for 3 weeks and having an empty box for that time, and i've installed all the programs i need and done a major update (134 updates in total) so i'm going to try not to 'apt-get update' unless absolutely necessary, and i won't install any new packages unless i absolutely need them.

can anyone give me any more tips on minimising the data usage ?

anything, no matter how dumb, would be useful .. thanks :D

---

### Post by ddrichardson on 2007-09-23
Get a new ISP is the first thing that springs to mind. That aside, turn off automatic updates, make sure there are no torrents downloading (if you use them), automatic podcast fetchers that sort of thing.

/tinfoilhat

40 Gb is still an awful lot to have achieved, with just apt-get in one month. If you're on a wireless connection, change the password just in case someone is hijacking your connection.

/tinfoilhat

---

### Post by jasonwatkins on 2007-09-24
i've switched off automatic updating, so that's a start, and i'm not on wireless either.

i know i was trying a LOT of different packages, both in synaptic and the add/remove programs option as well.

i also tried a few things out at getdeb.net as well.

there is one possibility that might have caused this issue though - as a fan of mystery science theatre 3000, i'm always looking for decent torrents for that to download and I found one that contained everything ever screened for the show at a size of 135gb.

I downloaded it and fired it up in deluge and basically de-selected everything bar 3 films - a grand total of 1.2gb - that I wanted, so i'm just wondering if deluge essentially 'clocked' it as a 135gb download before I had time to de-select all the files.

that is the main thing that stands out as the only other possibility.

---

### Post by hyper_ch on 2007-09-24
it's not so much the download more the upload that your ISP is probably complaining about. Normally only uploads make costs to the telcos hence we have here mostly asynchronous connections: I have 10mbit download but "only" 1mbit upload...

and if you use torrents you're also uploading...

---

### Post by ddrichardson on 2007-09-24
No, what deluge does or doesn't think a download is has nothing to do with how your ISP meters your usage. If you really don't think that your usage is that high then you need to discuss it with them.

---

### Post by jasonwatkins on 2007-09-24
> **hyper_ch said:**
> it's not so much the download more the upload that your ISP is probably complaining about. Normally only uploads make costs to the telcos hence we have here mostly asynchronous connections: I have 10mbit download but "only" 1mbit upload...

and if you use torrents you're also uploading...

yeah, i can see that - i'll have to look at deluge and see what's what.  maybe i can scale it down or something like that.

---

### Post by jasonwatkins on 2007-09-24
i'm looking at my deluge settings now, for bandwith.

i've got maximum connections set at 800
maximum download speed set at -1 (KiB/s) (i assume this means unlimited ..)
maximum upload speed is 1120 (KiB/s)
maximum upload slots is 25

on the per torrent bandwith usage,  both maximum connections and upload slots are both set to -1

i'm thinking off the top of my head maybe reducing the number of connections slightly, and lowering the upload speed .. would that do me any favours ?

---

### Post by jasonwatkins on 2007-09-24
i've set max connections to 500 and upload speed to 720, but the upload speeds still do seem significantly higher than downloads.

i guess if i'm effectively uploading twice as much as i'm downloading, that's another possible explanation

---

### Post by ddrichardson on 2007-09-24
With torrents you can find that speeds can be swamped by the acknowledging packets. Generally aim to around 25-30 % of observed download speed seems to give the best results. For example I use max download of 111kbps and a 26kbps upload speed.

Every time you send a packet out, a returned packet is recieved. But you'd need to uploading an awful lot.

---

### Post by jasonwatkins on 2007-09-27
ok, this is pissing me off now ..

i've just been running deluge and i had 17 seeds, 99 peers and 10 dht connections as well.

my download speed was 1.6 kb/s and my upload speed was 29.2 kb/s

i'd uploaded 5mb and downloaded about 800kb

i can't work out the settings in deluge to fix that - if i use ktorrent, it's not such an issue for some reason, but the download appears to be much slower and gives an estimated time of something like 2 days, as opposed to deluge's 15-20 hours ..

---

