---
title: "Bandwidth Limiter Manager thing!"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-05-12
I am after a application/tool, preferably command line.

I want to be able to manage bandwidth, eg

```

Port                    Upload                    Download
54354                   2                         2
484                     5                         1

```

Is there such a application? A web interface would be nice, but as I stand at the moment anything would be nice.

I would also note that the machine I am planning on running this on I am also using as a router, with masquerading setup. So something where I can also setup port forwarding, and limiting bandwidth for local machines would be perfect.

Does anyone know what I'm after, any advice would be awesome.

---

### Post by cryogen on 2007-05-12
> **guysmiley25 said:**
> Does anyone know what I'm after, any advice would be awesome.

Sounds like you're after QoS (Quality Of Service) or Traffic Shaping settings.  I'm not sure what packages would give this to you though, you might look at [wondershaper]("http://packages.debian.org/unstable/net/wondershaper") which sounds like what you want.

---

### Post by guysmiley25 on 2007-05-12
I've just installed windershaper and try it out. But it does not quite do what I want.

Here is part of the man:
```

SYNTAX
       A  summary  of  wondershaper  syntax is included below.  For a complete
       description, see the files in /usr/share/doc/wondershaper.

       wondershaper [ interface ]
              Shows the status of traffic shaping on that interface.

       wondershaper clear [ interface ]
              Removes all traffic shaping from that interface.

       wondershaper [ interface ] [ downlink ] [ uplink ]
              Configures the wondershaper on the  specified  interface,  given
              the  specified  downlink  speed  in kilobits per second, and the
              specified uplink speed in kilobits per second.

```

So it looks like you can limit upload speed, and download speed. However does not look like you can do it for individual ports.

---

### Post by Marsolin on 2007-05-12
[trickle]("http://linuxappfinder.com/package/trickle") is another alternative.

---

### Post by guysmiley25 on 2007-05-23
Now I could be wrong but I think the problem with trickle is that you have to run it at the time of running the application.

This is a pain and I want to do everything at the ports.

---

