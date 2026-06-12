---
title: "Replace refit with Grub2"
date: 2010-02-15
forum: Apple Hardware Users
---

### Post by cole.mickens on 2010-02-15
So, I'm not the world's biggest fan of rEFIt to be perfectly honest. It doesn't allow me to customize the menu, set a default, etc. I'd rather boot exclusively using grub-efi.

Not just that, I'd prefer to be able to do so without needing an hfs+ volume to bless it onto.

Can anyone offer instructions to accomplish this, or point me in the direction of such instructions?

Thank you!

**edit:** I can now see that Elv117 has asked this recently. I shall leave this post here in the hopes that someone knowledgable runs across it and not the one further down the page. Also, I'll probably try working through the tutorial to see if I can manage it. I need to evaluate if I really need OS X at all on my MacBook. I think it would be neat to have GPT/Grub2/MacOSX/Ubuntu/Win7 working properly, the way a "modern" computer ought to. Reverting to MBR is just throwing in the towel.

---

### Post by dennis123123 on 2010-02-18
This is *not* fact (just what I understand from what i've read); but I don't think you can get accelerated nvidia graphics with a direct EFI boot on a macbook at the moment.

Though I personally have never got it to boot the kernel, it hangs after it reads it :(

Its not yet ready for widespread use over mbr booting in this particular scenario.




If improvements have been made since I last experimented, someone knowledgable please reply :)

---

### Post by dmitrijledkov on 2010-02-18
I've managed to get grub2-efi to boot but it still needed to be blessed for Macbook firmware to pick it up. (google linus talking about macs and efi). Didn't have windows installed so mum there.

BTW in rEFIt you can have LegacyFirst config option to get the reverse order of choices...

---

### Post by cole.mickens on 2010-02-19
> **dmitrijledkov said:**
> I've managed to get grub2-efi to boot but it still needed to be blessed for Macbook firmware to pick it up. (google linus talking about macs and efi). Didn't have windows installed so mum there.

BTW in rEFIt you can have LegacyFirst config option to get the reverse order of choices...

When you say that it still has to be blessed, you mean that it still to be on an hfs+ partition. I guess I don't mind that (practically, I mind it from a principles standpoint) since I do still have OS X installed...

Speaking of which, for this to be done right, would one expect an EFI firmware to load grub.efi, say, from the EFI Fat32 partition? Any reasons Apple didn't implement it this way? Seems rather rude and presumptuous of them.

---

### Post by Elv13 on 2010-02-20
Can someone make a decent tutorial? The ones I found on google are quite outdated and not working. It ask to compile on Ubuntu and execute on OSX, those binary are incompatible, so I can't.

I have an HFS+ partition too, so I dont mind using it for grub2, but I don't know how to install it. Just using apt-get install grub2-efi make grub fail to start, blessing may work, but I don't know how.

And about nvidia, I have compiz running right now without NVIDIA binary driver, so it's not a blocker anymore, the Nouveau team done a good job. OpenGL stuff still run slow, but using XRender work at a nice speed.

---

### Post by dmitrijledkov on 2010-02-20
[http://grub.enbug.org/TestingOnMacbook]("http://grub.enbug.org/TestingOnMacbook")

efi firmware has nothing to do with mac <-> linux binary compatability for executables cause you are compiling firmware which can be understood by intel motherboard ;-)

---

### Post by dennis123123 on 2010-02-21
> **Elv13 said:**
> And about nvidia, I have compiz running right now without NVIDIA binary driver, so it's not a blocker anymore, the Nouveau team done a good job. OpenGL stuff still run slow, but using XRender work at a nice speed.

Thank you for detailing this. I agree they have done a great job, but there is still no way i'd settle for restricting graphics performance in favor of a slightly cleaner/faster boot :(

---

### Post by Elv13 on 2010-02-25
> **dmitrijledkov said:**
> [http://grub.enbug.org/TestingOnMacbook]("http://grub.enbug.org/TestingOnMacbook")

efi firmware has nothing to do with mac <-> linux binary compatability for executables cause you are compiling firmware which can be understood by intel motherboard ;-)

This command:
./grub-mkimage -d . -o grub.efi part_gpt hfsplus fat ext2 normal sh chain boot configfile linux
sudo cp grub.efi *.mod *.lst /Volumes/something/efi/grub

say invalid binary when I try to run it in OSX. It is what I am talking about.

---

