---
title: "No sound on Toshiba Satellite 4020CDT"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by zip_000 on 2006-03-22
I've recently installed Ububtu on a fairly old laptop, and it is working well (if slow (it is a very old laptop)) except for the complete lack of sound.

My question is, how do I find out if I can even have audio on this laptop? (I'm a newbie obviously). It has speakers and ear piercing beeps, but I don't know if that means it hreally has audio.

I'm not even looking for it to have working speakers, I just want to be able to plug in earphones and here something. 

Whenever I try to play any audio files I get an error, I'm at work now and I can't check exactly what the error is, but I will post it later.

Any help will be appreciated!

---

### Post by Brunellus on 2006-03-22
do you hear drums when you get to the main login screen?

---

### Post by zip_000 on 2006-03-23
Nope no drums.

With Totem, I keep getting an error that says:
"Failed to play: could not open resource for writing"

With Rhythmbox, I don't get an error, but it doesn't play either - it will bring up the file as if it were about to play, but it never does.

With sound juicer. I get: "Error playing cd: Reason: Could not open resource for writing"

My initial thoughts (and I know very little about this) are that either:
1) There is a permission that I need to grant that I haven't (I've tried that but maybe I did it wrong)
2) I don't have any sort of sound on this computer

Of course I have no idea :-\

Thanks!

---

### Post by akiro.yamamoto on 2006-03-23
Post the output of:
```

lspci | grep -i audio

```

---

### Post by akiro.yamamoto on 2006-03-23
Here is a pic of mine :)

---

### Post by zip_000 on 2006-03-23
Um, yeah - there isn't any output from that...which I'm guessing isn't good.

Here is the out put from just lspci if that could help any:
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 02)
0000:00:02.0 CardBus bridge: Toshiba America Info Systems ToPIC97 (rev 05)
0000:00:02.1 CardBus bridge: Toshiba America Info Systems ToPIC97 (rev 05)
0000:00:04.0 VGA compatible controller: Chips and Technologies F65555 HiQVPro (rev c6)
0000:00:07.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0a.0 Communication controller: Toshiba America Info Systems FIR Port (rev 23)
0000:05:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

---

