---
title: "the perfect server  but no localhost"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by synistics on 2008-01-08
I went to another site that had step by step on the perfect server install.

everything worked great BUT

I cannot find the localhost. No ping, no web, nothing will bring it up.

That really puts a challenge on getting phpmyadmin up and running or Drupal.

what should I be looking for?  What have I done that would put the localhost out of reach?

TIA

---

### Post by Pevichaey5 on 2008-01-08
hey

i'm assuming you are using apache correct?

what version are you using?

---

### Post by bwhite82 on 2008-01-08
Goto the CLI and type:

sudo ifconfig lo

To see if it brings it up. This is an odd one to me. Have to ask: you tried to ping 127.0.0.1, right?

---

### Post by smartalecks on 2008-01-08
can you link to the instructions you used, thanks

---

### Post by synistics on 2008-01-09
after posting here I got a repeated error on the host.conf, rebooted and everything is fine now, !@& is there, apache is working fine and phpmyadmin is working again.

Thanks for at least reading through and some suggestions.

---

