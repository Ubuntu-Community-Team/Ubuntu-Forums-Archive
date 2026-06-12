---
title: "Restoring OSX (i.e. no yaboot)"
date: 2009-06-08
forum: Apple Hardware Users
---

### Post by danleong on 2009-06-08
Hello,

I'd like to revert from my dual-boot OSX/Ubuntu 9 to just OSX. It's not that I hate Linux, I love it :) However this Powerbook G4 is going to someone who just wants a normal Mac.

Is there anyway to get rid of yaboot and just get the original boot loader restored?

diskutil list :-
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     Apple_partition_scheme                        *149.1 Gi   disk0
   1:        Apple_partition_map                         31.5 Ki    disk0s1
   2:                  Apple_HFS Mac OS X                110.0 Gi   disk0s3
   3:            Apple_Bootstrap                         977.0 Ki   disk0s4
(disk0s5 and disk0s6 were ubuntu)

OF boot-device    /pci@f4000000/ata-6@d/disk@0:2,\\:tbxi

Q: Can I delete Apple_Bootstrap safely ?
Q: Can I do some OF setenv to boot from disk0s3 ?

Thanks for any help you can offer,
Dan

---

### Post by tiresia on 2009-06-08
> **danleong said:**
> Q: Can I delete Apple_Bootstrap safely? Yes
> Q: Can I do some OF setenv to boot from disk0s3 ?You don't need to do anything - if you have problems, reset PRAM parameters (cmd-opt-P-R at boot up)

---

### Post by MikeTheC on 2009-06-08
> **tiresia said:**
> Yes
You don't need to do anything - if you have problems, reset PRAM parameters (ctr-alt-P-R at boot up)

Nope, that's CMD+OPT+P+R. Option is the more proper name for the Alt key on a Mac, and Control and Command are two completely different keys.

---

### Post by tiresia on 2009-06-08
> **MikeTheC said:**
> Nope, that's CMD+OPT+P+R. Option is the more proper name for the Alt key on a Mac, and Control and Command are two completely different keys.
Right! I wrote too fast ;) 
I corrected it. Thanks

---

