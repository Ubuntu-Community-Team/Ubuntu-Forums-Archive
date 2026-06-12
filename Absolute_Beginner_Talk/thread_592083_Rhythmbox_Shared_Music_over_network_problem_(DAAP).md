---
title: "Rhythmbox: Shared Music over network problem (DAAP)"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by econmit on 2007-10-26
I recently installed Gusty and am loving the switch from XP!

One issue I have not been able to solve yet:

I have managed to get MP3 files on my own computer to play (I have gstream and ubuntu-restricted-extras). But I have not been able to make Rhythmbox play shared music from other machines on my local network (using iTunes). I can see the shared folders but when I click on them I do not get a list of tracks. It says "retrieving songs from music share" but no tracks appear.

Any ideas? Am I missing some package?

---

### Post by julian67 on 2007-10-26
[http://en.wikipedia.org/wiki/ITunes]("http://en.wikipedia.org/wiki/ITunes")

> With the release of iTunes 7.0, Apple changed their implementation of DAAP. This change prevents any third-party client, such as a computer running Linux, a modified Xbox, or any computer without iTunes installed, from connecting to a remote iTunes repository. iTunes will still connect as a client to other iTunes servers and to third-party servers

Check your version of iTunes.

---

### Post by econmit on 2007-10-26
Thanks. They are all iTunes 7.x What a nasty move by Apple. 

Is there any workaround for this?

---

### Post by jusmurph on 2007-10-26
Go Go DRM.

I beat there is a "Bug" report on the launchpad about such problems.

---

### Post by fcumok on 2007-10-26
Or an alternative? I'd love to be able to stream my MP3's from my mac.

---

### Post by julian67 on 2007-10-26
> **econmit said:**
> Thanks. They are all iTunes 7.x What a nasty move by Apple. 

They get far too much uncritical coverage and this is a good reminder that proprietary companies need show no respect for their customers. This happened a while ago and afaik there was no reason except sheer unpleasantness for making this change.

edit: I believe the workaround is to uninstall Apple OS from the computers and install free software in its place.

---

### Post by fcumok on 2007-10-27
> **julian67 said:**
> They get far too much uncritical coverage and this is a good reminder that proprietary companies need show no respect for their customers. This happened a while ago and afaik there was no reason except sheer unpleasantness for making this change.

edit: I believe the workaround is to uninstall Apple OS from the computers and install free software in its place.

The trouble with that is the free software is no where near in stability or ease of use. Until that day open source needs to work with proprietary :roll:

---

### Post by julian67 on 2007-10-27
> **fcumok said:**
> The trouble with that is the free software is no where near in stability or ease of use. Until that day open source needs to work with proprietary :roll:

You've missed the point.  

When Apple locked other DAAP protocols out of access to iTunes repositories this wasn't a proprietary vs free issue, they also excluded Microsoft products which use DAAP. This has absolutely nothing to do with "stability or ease of use", but everything to do with a proprietary vendor (Apple) who now feels dominant enough in the personal audio arena to start flexing their muscles and finding ways to lock their customers *in* and other companies products *out*.  

This kind of behaviour is completely typical of any monopolist or would-be monopolist in any area of commerce, politics, religion etc. It makes a nice illustration of the penalties of using proprietary software and why interoperability across platforms can't be assured with closed standards. You can't rely on the goodwill of people or corporations that have no respect for you.

---

### Post by fcumok on 2007-10-27
> **julian67 said:**
> You've missed the point.  

When Apple locked other DAAP protocols out of access to iTunes repositories this wasn't a proprietary vs free issue, they also excluded Microsoft products which use DAAP. This has absolutely nothing to do with "stability or ease of use", but everything to do with a proprietary vendor (Apple) who now feels dominant enough in the personal audio arena to start flexing their muscles and finding ways to lock their customers *in* and other companies products *out*.  

This kind of behaviour is completely typical of any monopolist or would-be monopolist in any area of commerce, politics, religion etc. It makes a nice illustration of the penalties of using proprietary software and why interoperability across platforms can't be assured with closed standards. You can't rely on the goodwill of people or corporations that have no respect for you.

I'm not saying I disagree with that and yes apple should help towards working with interoperability however we're in a situation where potential new linux users would be turned away from using a new OS because of this. Microsoft users can do this by using itunes, we're unable to do that.

---

### Post by julian67 on 2007-10-27
> **fcumok said:**
> I'm not saying I disagree with that and yes apple should help towards working with interoperability however we're in a situation where potential new linux users would be turned away from using a new OS because of this. Microsoft users can do this by using itunes, we're unable to do that.

Yes it would be nice to live in the world where Apple felt like they "should help". But actually for 100% selfish reasons they broke something that many of their own customers use and they could do it because they own the proprietary protocol. The solution is clearly not to give them more power by introducing their protocols into our world, or to feel that this is an inadequacy of the free desktop. The solution is actually in progress and is the greater adoption of free software and equally importantly the understanding of what that freedom means.  There aren't many cases as clear as this one where a proprietary vendor deliberately sabotages the enjoyment of many of its own customers and their friends and associates. Companies like Apple and MS just see you as a person who might make them a profit (or several). To them you aren't part of a society or a community, you're just a financial potential. Conversely free software is *designed* to let you be a good neighbour, it respects the fact that you don't exist in isolation and that you are part of a community. It's right there in the gpl preamble. 

> The licenses for most software are designed to take away your
freedom to share and change it.  By contrast, the GNU General Public
License is intended to guarantee your freedom to share and change free
software--to make sure the software is free for all its users. 

---

### Post by dmber on 2007-11-03
install gutsy on your mac...

that did the trick for me :)

---

### Post by tjansson on 2007-11-13
Just encountered the same problem. Glad to know that it is a iTunes problem and not something in Rhythmbox even though it sad that Apple changed it.

---

