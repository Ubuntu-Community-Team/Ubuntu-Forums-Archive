---
title: "Creative Vision M"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by notrenneks on 2006-11-16
Hi,
I'm fairly new to linux and I've been trying unsuccessfully for a while now to get my Creative  vision M mp3 player to work with amarok and edgy.  Ive been able to get it to work with gnomad2 but would love it to work with amarok.  Also whenever I connect my mp3 player it keeps detecting it as a digital camera and crash's if i try and import photos whats up with that and how do i fix it.  Sorry for the long thread I just really want to get this fixed.

---

### Post by Marsolin on 2006-11-16
What version of [Amarok]("http://linuxappfinder.com/package/amarok") are you running? I'd suggest 1.4.2 or higher. [libmtp]("http://libmtp.sourceforge.net/") is supported starting with that version. In Edgy it's called libmtp2.

---

### Post by notrenneks on 2006-11-16
Hi,
I'm running Amarok 1.4.4 and have libmtp2 installed.  I'm sure i'm missing something simple just wish i knew what.

---

### Post by NESFreak on 2006-11-22
ubuntu's amarok isn't compiled with libmtp support. Trying to find out myself how to fix it. (without installing the full kde-dev suite and half of the normal kde)

NESFreak

---

### Post by TriggerHappyChewie on 2006-12-17
Compile Amarok from source.  Grab the latest source from their website, and make sure to enable  libmtp support with configure.

---

### Post by msak007 on 2006-12-17
I have the same problem with a Zen MicroPhoto. Kubuntu detects is as a camera and I can transfer files to it, I can compile Gnomad with libmtp and get it to work, but Amarok is a different beast and I haven't attempted to compile it yet. I don't know much about packaging software for the repos but I think at this stage in the game with so many people having MTP devices, the versions of both Amarok and Gnomad in the repositories should be compiled with libmtp support. It's not like it really adds that many extra dependencies, just libmtp. I don't know about other distros, but I think removing this additional roadblock to being able to use your hardware OOTB would be in line with Ubuntu's goals of making it easy for the average user.

---

### Post by freddybob on 2006-12-18
> **TriggerHappyChewie said:**
> Compile Amarok from source.  Grab the latest source from their website, and make sure to enable  libmtp support with configure.

Sorry if this is a stupid question (this is the Absolute Beginner forum) but how do I do what you suggest?  Does anyone have step-by-step instructions?

I found step-by-step instructions for Gnomad2 and it now plays nice with my Creative Zen Touch, but I'd like to use Amarok and MTP on Edgy as well.

**Oops, I should have searched harder, the instructions are here: [http://ubuntuforums.org/showthread.php?t=316246](http://ubuntuforums.org/showthread.php?t=316246)**

---

