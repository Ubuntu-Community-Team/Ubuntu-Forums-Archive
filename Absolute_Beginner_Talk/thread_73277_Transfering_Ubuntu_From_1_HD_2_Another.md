---
title: "Transfering Ubuntu From 1 HD 2 Another?"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by nitricacid on 2005-10-08
Is there anyway I can transfer my installed ubuntu that I have on my 40gig HD to my 80gig HD that is in the same computer?

I have been waiting for the full release of breezy to come out and just install it on my 80Gig drive so i can pull my 40gig HD out and use it in my PS2 but then i thought. Why should i do that if i can transfer all my settings. Instead of having to re-adjust everything back to the way i have it now.

I do not have a duel boot machine. One HD runs windblows the other Ubuntu.

---

### Post by Kyral on 2005-10-08
IN THEORY (Read as it SHOULD work, but no promises) if you just recreate your partition table on the second HD then just cp the entire / over to it, it might work...

or you could try something like dd if=/dev/xxx of=/dev/XXX but I dunno I just skimmed the dd manpage...

---

### Post by zerhacke on 2005-10-08
If you went the DD way I would assume you would need to accomodate transferral of the bootsectors as well.

count 512...something like that...I'll google and be back.

---

