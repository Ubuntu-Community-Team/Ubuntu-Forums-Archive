---
title: "Ubuntu Firefox Google problem"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by getut on 2007-07-05
Is anyone having issues getting to google with Firefox in Ubuntu? I can get there just fine wtih IE in windows and Firefox in windows from the same IP address.

Ever since yesterday morning, If I try to go to [www.google.com](www.google.com), I get forwarded to a new url: [http://www.google.com/sorry/?continue=http://www.google.com/](http://www.google.com/sorry/?continue=http://www.google.com/)

We're sorry but your query looks similar to automated requests from a computer virus or spyware application.

I looked at the request with wireshark, nothing fishy appears to be going  on. So the spyware/virus warning appears bogus.

0000   00 10 db 75 da 20 00 16 d4 ba 32 85 08 00 45 00  ...u. ....2...E.
0010   01 d2 49 bb 40 00 40 06 4c d9 ac 16 05 50 d0 45  ..I.@.@.L....P.E
0020   20 e6 ca 7b 00 50 9f 3b 52 21 ce 7e 64 0f 80 18   ..{.P.;R!.~d...
0030   00 b7 a4 56 00 00 01 01 08 0a 0a 3e 1b b9 6c 8e  ...V.......>..l.
0040   52 86 47 45 54 20 2f 20 48 54 54 50 2f 31 2e 31  R.GET / HTTP/1.1
0050   0d 0a 48 6f 73 74 3a 20 77 77 77 2e 67 6f 6f 67  ..Host: [www.goog](www.goog)
0060   6c 65 2e 63 6f 6d 0d 0a 55 73 65 72 2d 41 67 65  le.com..User-Age
0070   6e 74 3a 20 4d 6f 7a 69 6c 6c 61 2f 35 2e 30 20  nt: Mozilla/5.0 
0080   28 58 31 31 3b 20 55 3b 20 4c 69 6e 75 78 20 69  (X11; U; Linux i
0090   36 38 36 3b 20 65 6e 2d 55 53 3b 20 72 76 3a 31  686; en-US; rv:1
00a0   2e 38 2e 31 2e 34 29 20 47 65 63 6b 6f 2f 32 30  .8.1.4) Gecko/20
00b0   30 36 31 32 30 31 20 46 69 72 65 66 6f 78 2f 32  061201 Firefox/2
00c0   2e 30 2e 30 2e 34 20 28 55 62 75 6e 74 75 2d 66  .0.0.4 (Ubuntu-f
00d0   65 69 73 74 79 29 0d 0a 41 63 63 65 70 74 3a 20  eisty)..Accept: 
00e0   74 65 78 74 2f 78 6d 6c 2c 61 70 70 6c 69 63 61  text/xml,applica
00f0   74 69 6f 6e 2f 78 6d 6c 2c 61 70 70 6c 69 63 61  tion/xml,applica
0100   74 69 6f 6e 2f 78 68 74 6d 6c 2b 78 6d 6c 2c 74  tion/xhtml+xml,t
0110   65 78 74 2f 68 74 6d 6c 3b 71 3d 30 2e 39 2c 74  ext/html;q=0.9,t
0120   65 78 74 2f 70 6c 61 69 6e 3b 71 3d 30 2e 38 2c  ext/plain;q=0.8,
0130   69 6d 61 67 65 2f 70 6e 67 2c 2a 2f 2a 3b 71 3d  image/png,*/*;q=
0140   30 2e 35 0d 0a 41 63 63 65 70 74 2d 4c 61 6e 67  0.5..Accept-Lang
0150   75 61 67 65 3a 20 65 6e 2d 75 73 2c 65 6e 3b 71  uage: en-us,en;q
0160   3d 30 2e 35 0d 0a 41 63 63 65 70 74 2d 45 6e 63  =0.5..Accept-Enc
0170   6f 64 69 6e 67 3a 20 67 7a 69 70 2c 64 65 66 6c  oding: gzip,defl
0180   61 74 65 0d 0a 41 63 63 65 70 74 2d 43 68 61 72  ate..Accept-Char
0190   73 65 74 3a 20 49 53 4f 2d 38 38 35 39 2d 31 2c  set: ISO-8859-1,
01a0   75 74 66 2d 38 3b 71 3d 30 2e 37 2c 2a 3b 71 3d  utf-8;q=0.7,*;q=
01b0   30 2e 37 0d 0a 4b 65 65 70 2d 41 6c 69 76 65 3a  0.7..Keep-Alive:
01c0   20 33 30 30 0d 0a 43 6f 6e 6e 65 63 74 69 6f 6e   300..Connection
01d0   3a 20 6b 65 65 70 2d 61 6c 69 76 65 0d 0a 0d 0a  : keep-alive....
01e0

---

### Post by moredhel on 2007-07-05
Have you tried in something else like opera/galeon/epiphany/galeon?

---

### Post by lisati on 2007-07-05
I tried the "sorry" link and got a message saying that it wasn't ound.... I'm not sure what's going on.

---

### Post by skymera on 2007-07-05
maybe you have spyware in windows that uses google???

---

### Post by sailor2001 on 2007-07-05
download swiftweasel

---

### Post by Moop on 2007-07-05
Have you tried clearing your cookies in Firefox?

---

### Post by getut on 2007-07-05
Well.. strangely enough it is better again.

Yesterday morning it did the redirect and spyware warning, then yesterday evening it was all better again, but this morning the redirect was back, thus my post asking about it.

Its after lunch time here and Google is working normally again. I haven't changed anything at any point during all of this.

Another strange symptom... I am behind a corporate proxy server, but I am in IT so I have the  option of going around it :D. I use the proxy button Firefox addon to toggle between proxied and un-proxied.

When the problem has shown up the last two mornings, it showed up when going direct. I could switch to being behind the proxy and Google would work normally. Go back to going direct and the problem would be back. Then later that evening, no problem either proxied or unproxied.

---

