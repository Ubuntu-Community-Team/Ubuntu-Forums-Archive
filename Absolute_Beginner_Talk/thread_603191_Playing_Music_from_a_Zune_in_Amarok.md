---
title: "Playing Music from a Zune in Amarok"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by It_Was_Luck on 2007-11-04
Well I spent a long time today trying to figure out how to get Amarok to detect my Zune plugged it. And I finally got it. I just called it a MTP Media Device, then when I search it finds my Zune! And it loads all the music.

So I go to play a song and it says "Some Media Could Not Be played (not playable)"
And every song says that. So I was wondering if anyone knew how I could get mysic from my Zune to play in Amarok. I got it to appear in amarok, but it won't play.

---

### Post by tgalati4 on 2007-11-04
If the music is encoded in something other than *.mp3 or *.ogg then it's doubtful that it will play correctly.  If you loaded your Zune using the Zune software, then all of the music is probably infected with Digial Rights Management (DRM).  That means you can't play it anywhere else--except on the Zune.

---

### Post by trickykungfu on 2007-11-12
It doesn't have anything to do with the format of the music.  The Zune requires authentication to transfer files, and as of yet that hasn't been cracked.  See [http://libmtp.sourceforge.net/](http://libmtp.sourceforge.net/) for more information; that's the library that Amarok uses to talk to the Zune and other MTP devices.

---

### Post by T2manner on 2008-05-03
>   trickykungfu
  Re: Playing Music from a Zune in Amarok
 It doesn't have anything to do with the format of the music. The Zune requires authentication to transfer files, and as of yet that hasn't been cracked. See [http://libmtp.sourceforge.net/](http://libmtp.sourceforge.net/) for more information; that's the library that Amarok uses to talk to the Zune and other MTP devices.

actually it does have a lot to do with the format of the music.
there is a subscription deal with the zune marketplace which gives the user unlimited downloads, but not complete owning rights of the music, which results in the files being encoded with DMR.
this can only be played with the zune.

---

### Post by Luinfana on 2008-06-02
@T2Manner

Although there *can* be DRM involved with the Zune (such as with Zune Pass as you mentioned), the issue at hand is why music will list, but not play **in general** from the device. In this respect, trickykungfu is correct - the problem is with the Zune's MTP handshake, used to authenticate file transfers. Only after this handshake can be replicated in some way will the Zune work fully with libmtp. At that point there should be no reason why Amarok or any other audio player should have any problem reading MP3s or WMAs from the device unless they have been purchased from Zune Marketplace.

---

