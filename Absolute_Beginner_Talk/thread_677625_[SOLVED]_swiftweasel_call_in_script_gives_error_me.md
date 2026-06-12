---
title: "[SOLVED] swiftweasel call in script gives error message"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by johnraff on 2008-01-25
I've got a script which resizes images, helps me edit html files and uploads everything to my website - it all seems to be working OK except that right at the end I call swiftweasel to check if the page looks OK with ```
#(edit, upload etc)
swiftweasel http://www.*mydomain*.com &
exit 0
```
If I run the script in a terminal I get ```
*prompt*$ esd: no process killed
the settings directory exists
```
I have to use control+C to get the prompt back.

Can this be fixed?
Does it matter?

(I'm using Swiftweasel 2.0.0.11 pentium3 build.)

---

### Post by markyb86 on 2008-01-25
what about

```
swiftweasel %u http://www.mydomain.com &
```

---

### Post by johnraff on 2008-01-25
> **markyb86 said:**
> what about

```
swiftweasel %u http://www.mydomain.com &
```
Hmm that's interesting. Trying the command in a terminal:
*it gives the same error message, but
*gives me back the prompt
*opens swiftweasel in a new window, not a new tab in the current window
*opens two tabs in that window, one trying to connect to "www.%u.com", the other (sucessfully) to [www.mydomain.com](www.mydomain.com)

???

Not sure if this is a swiftweasel issue (firefox gives no errors) or an ubuntu issue;
either way I suppose it's something I could live with as long as massive resources aren't being tied up in the background or something.

---

### Post by markyb86 on 2008-01-26
I have noticed it does that (the two tabs, one as %u and the other the site I need) when I set swiftfox as my default browser

---

### Post by johnraff on 2008-01-26
> **markyb86 said:**
> I have noticed it does that (the two tabs, one as %u and the other the site I need) when I set swiftfox as my default browseras mine indeed is.

---

### Post by Kilz on 2008-01-26
> **johnraff said:**
> Hmm that's interesting. Trying the command in a terminal:
*it gives the same error message, but
*gives me back the prompt
*opens swiftweasel in a new window, not a new tab in the current window
*opens two tabs in that window, one trying to connect to "www.%u.com", the other (sucessfully) to [www.mydomain.com](www.mydomain.com)

???

Not sure if this is a swiftweasel issue (firefox gives no errors) or an ubuntu issue;
either way I suppose it's something I could live with as long as massive resources aren't being tied up in the background or something.

The esd error message is because its attempting to kill any sound that may be being playing. This is so that flash can use it. The error message is nothing to be concerned about. If you want it to go away (but then flash may have no sound if you have something else using sound when you start the browser). Just comment out the 
```
killall esd
```
line in /usr/bin/swiftweasel by placing a # in front of it and saving the file.

---

### Post by johnraff on 2008-01-29
> **Kilz said:**
> The esd error message is because its attempting to kill any sound that may be being playing. This is so that flash can use it. The error message is nothing to be concerned about. If you want it to go away (but then flash may have no sound if you have something else using sound when you start the browser). Just comment out the 
```
killall esd
```
line in /usr/bin/swiftweasel by placing a # in front of it and saving the file.Aah... that's the culprit! Thanks for that (though it's in /usr/local/bin on my box).
A quick look at man killall suggested modifying that line to```
killall -q esd
```
Now I get no error message, and hopefully no flash sound problems. :)

---

