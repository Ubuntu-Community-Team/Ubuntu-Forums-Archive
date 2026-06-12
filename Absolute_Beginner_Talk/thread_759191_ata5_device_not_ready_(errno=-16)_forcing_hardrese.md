---
title: "ata5: device not ready (errno=-16) forcing hardreset"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by analoog on 2008-04-18
```

Apr 19 02:32:01 broom kernel: [183079.759564] ata5.00: status: { DRDY }
Apr 19 02:32:06 broom kernel: [183084.795222] ata5: port is slow to respond, please be patient (Status 0xd0)
Apr 19 02:32:11 broom kernel: [183089.775967] ata5: device not ready (errno=-16), forcing hardreset
Apr 19 02:32:11 broom kernel: [183089.775981] ata5: soft resetting link
Apr 19 02:32:11 broom kernel: [183090.300100] ata5.00: configured for MWDMA2
Apr 19 02:32:11 broom kernel: [183090.300130] ata5: EH complete

```

I'm getting this error in my dmesg and kernel.log. It happens a lot of times (like 3 times a minute)
When I google for it I see a lot of people with that error. and a lot of possible solutions. 
Only I'm confused what my ata5 device actually is, I guess my harddisk?
how can I check this? 
And what is this error about? 

thanks :)

---

