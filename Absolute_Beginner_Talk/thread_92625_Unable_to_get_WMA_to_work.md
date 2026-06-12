---
title: "Unable to get WMA to work"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by The Maste on 2005-11-20
I'm sure everyone has seen their fair share of "I can't get WMA to work. Plz help!" Well, this is probably *another* one of those.

I have been on this problem for about 3 days. I'm able to install WMA support for every player including: xmms, beep media player, xine, etc. However, it seems every time I try to play a WMA or look at the file's information, regardless of the program I'm using (every one of them!), the program just disappears. Crash? I don't know. I can't figure this one out.

Any suggestions as what the cause may be?

---

### Post by aysiu on 2005-11-20
Maybe these links may help?
[http://www.ubuntuforums.org/showthread.php?t=90208&highlight=wma](http://www.ubuntuforums.org/showthread.php?t=90208&highlight=wma)
[http://www.ubuntuforums.org/showthread.php?t=79539&highlight=wma](http://www.ubuntuforums.org/showthread.php?t=79539&highlight=wma)

---

### Post by The Maste on 2005-11-20
Thank you for replying so quickly. I was easily able to eliminate a whole lot of other factors that may have been causing the problem much quicker with your help. I later found out that it had nothing to do with a hardware misconfiguration or that I had compiled the WMA plug-ins incorrectly.

I believe the strange "crashing" behaviour is attributed to the way that some of the WMAs were encoded. It would play some WMAs, but not all. The newer WMA files were the ones that were crashing every app. This leads me to believe that it's something to do with the newer encoding methods. Here is a snippet between WMA files that work and don't work, respectively:

Working WMA:
Filename: L:\mp3s\RPG\Final Fantasy\FF 87-94\FF5 d1 0217.wav.wma
Filesize: 1995865 bytes
Bitrate: 129032 bps
Seekable: true
Stridable: false
Broadcast: false
Is_Protected: false
Is_Trusted: false
Signature_Name:
HasAudio: true
HasImage: false
HasScript: false
HasVideo: false
CurrentBitrate: 129032
OptimalBitrate: 129032
HasAttachedImages: false
Can_Skip_Backward: false
Can_Skip_Forward: false
HasArbitraryDataStream: false
HasFileTransferStream: false
WM/ContainerFormat: 1

--------------------

Non-working WMA:
Filename: L:\mp3s\RPG\Final Fantasy\FFVII_Advent_Children_Soundtrack\Disk1\01 Opening.wma
Filesize: 8422659 bytes
Bitrate: 908938 bps
Seekable: true
Stridable: false
Broadcast: false
Is_Protected: false
Is_Trusted: false
Signature_Name:
HasAudio: true
HasImage: false
HasScript: false
HasVideo: false
CurrentBitrate: 738526
OptimalBitrate: 738526
HasAttachedImages: false
Can_Skip_Backward: false
Can_Skip_Forward: false
HasArbitraryDataStream: false
HasFileTransferStream: false
WM/ContainerFormat: 1
Title: Opening
Author: Noboru Uematsu
WM/Track: 0
WM/Lyrics:
WM/MediaPrimaryClassID: {D1607DBC-E323-4BE2-86A1-48A42A28441E}
WMFSDKVersion: 9.00.00.3250
WMFSDKNeeded: 0.0.0.0000
IsVBR: true
ASFLeakyBucketPairs: binary data
WM/TrackNumber: 1
WM/UniqueFileIdentifier: ;
WM/AlbumTitle: FINAL FANTASY ? ADVENT CHILDREN
WM/AlbumArtist: Noboru Uematsu
WM/MCDI: binary data
WM/Provider: User Feedback

Now, I may be wrong. But I can't think of any other reason for it not working. Both WMA files were not encoded to be "protected."

I ended up converting the problematic WMA files to OGG. If you are like me, transitioning from Windows, and can still boot into Windows I suggest downloading a program from this site: [http://www.litexmedia.com/audio_wizard/](http://www.litexmedia.com/audio_wizard/)

It encoded all of the files just fine without any noticable loss of quality. Of course there are restrictions as to how many files you can encode at one time, but I figure for someone just coming into this problem you would be saving yourself a whole lot of time just converting the files rather than banging your head trying to figure out why some WMA files play and some don't.

---

