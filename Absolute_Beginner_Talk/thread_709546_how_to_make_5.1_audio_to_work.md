---
title: "how to make 5.1 audio to work?"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by baysl on 2008-02-27
Only 2 speakers and woffer is working.

How do I make all 5 speakers to work?

---

### Post by Afkpuz on 2008-02-27
If your sound card is capable, then this should do it.

```
sudo gedit ~/.asoundrc

```

Paste this in below any other lines (if applicable)

```

pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}


pcm.analog {
    type plug
    slave analog_slave;
}

pcm_slave.analog_slave {
        pcm surround51;
        format S32_LE;
}
```

That should make your sound come all your speakers.  It also makes your movie players able to play in surround mode.  I'm not sure how to get a mixer with individual speaker settings though.

---

### Post by baysl on 2008-02-27
When I open it, there is no text inside-its empty document?

---

### Post by Afkpuz on 2008-02-27
Yeah, thats why I said "if applicable"

---

