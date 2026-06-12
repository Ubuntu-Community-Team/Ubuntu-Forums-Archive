---
title: "Port forwarding on Linksys router"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-07-28
Ok now for my dumb question of the night. I have satellite broadband (or so they say it's broadband) and my download speeds seem verrry slow. I have seen speeds up to 300 kb/s but usually they are below 100. I was under the impression the speeds should be around 700 kb/s. Any way should I do some port configuration on my router? Port scan using Network Tools shows port 80 the only one open on the router, and no port 80 open on my Gateway desktop or Toshiba laptop. The comps are all ethernet wired (no wireless at all). Bear with me as this is over my head. Thanks for the help.

---

### Post by felicity on 2007-07-28
Are you asking this question in reference to port 80 specifically? That is, are the download speeds you refer to being slow simply web-based downloads from port 80? If so, I don't think it would help to forward that port as it should either be open or be closed, i.e. you download full-speed or not at all. It's possible that your internet provider just has confusing advertisements in regards to the actual speeds.

---

### Post by jerrynewt on 2007-07-28
When downloading programs thru synaptic or add remove or even automatix (which I seldom use anymore) the download speed runs anywhere between less that 1 kb/s to 100 kb/s. I have seen it briefly jump to 200 for a second or two but rarely. Just asking if it could be port related or not. Like I said it's over my head -- looking for advice. Thanks again.

---

### Post by felicity on 2007-07-28
Those are about normal speeds for me too when downloading programs from the repository servers, though my connection is much higher. You might try a [speed test]("http://www.speakeasy.net/speedtest/") to find out what your speed is.

---

### Post by tomcheng76 on 2007-07-28
where are you now ?
you should choose a apt repositories that is near u

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)

---

### Post by sad_iq on 2007-07-28
To answer this: port 80 shows as open in the linksys because you can configure it via it's web-based interface..if you scan the router from the internet it will show as closed(it should be closed...double check.). Also      check your router...maybe it has some setting you need to change to allow a higher download speed(mine has something like ADSL, ADSL 2+ ...). And the speeds they advertise are theoretical, they provide a sustained speed (your connection will always download at x Kb/s) and a peak speed(don't remember the real name right now) in witch your speed cannot pass y Kb/s. Wasn't satellite connection supposed to be much faster than conventional ones?? Maybe your router can't handle that. Also isn't satellite connection supposed to work with a satellite dish or something???(are you sure it's satellite connection?? you need 2 isp's for that don't you???). Also if you can post the name of your provider...we'll look through their web page to see if there's something  relevant there!!!

---

### Post by tomcheng76 on 2007-07-28
```

gksudo synaptic&

```
Settings -> Repositories 
In "Ubuntu Software" Tab
choose download from ,then other
choose a server that is near you

---

