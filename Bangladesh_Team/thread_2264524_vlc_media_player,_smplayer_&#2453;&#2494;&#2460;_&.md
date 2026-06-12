---
title: "vlc media player, smplayer &#2453;&#2494;&#2460; &#2453;&#2480;&#2459;&#2503; &#2472;&#2494;&#2404; &#2489;&#2503;&#2482;&#2509;&#2474; &#2474;&#2509;&#2482;&#2495;&#2460;"
date: 2015-02-08
forum: Bangladesh Team
---

### Post by Ahanaf on 2015-02-08
vlc, smplayer &#2470;&#2495;&#2527;&#2503; &#2453;&#2507;&#2472; &#2477;&#2495;&#2465;&#2495;&#2451; &#2451;&#2474;&#2503;&#2472; &#2489;&#2458;&#2509;&#2459;&#2503; &#2472;&#2494;&#2404; &#2453;&#2507;&#2472; &#2477;&#2495;&#2465;&#2495;&#2451; &#2451;&#2474;&#2503;&#2472; &#2453;&#2480;&#2468;&#2503; &#2455;&#2503;&#2482;&#2503; &#2447;&#2453; &#2474;&#2482;&#2453; &#2447;&#2488;&#2503; &#2438;&#2476;&#2494;&#2480; &#2472;&#2494;&#2439; &#2489;&#2527;&#2503; &#2479;&#2494;&#2458;&#2509;&#2459;&#2503;&#2404; &#2453;&#2495;&#2472;&#2509;&#2468;&#2497; &#2476;&#2495;&#2482;&#2509;&#2463; &#2439;&#2472; &#2474;&#2509;&#2482;&#2503;&#2527;&#2494;&#2480; &#2470;&#2495;&#2527;&#2503; &#2474;&#2509;&#2482;&#2503; &#2489;&#2458;&#2509;&#2459;&#2503;&#2404; &#2447;&#2454;&#2472; &#2453;&#2495;&#2477;&#2494;&#2476;&#2503; &#2438;&#2478;&#2495; &#2447;&#2439; &#2474;&#2509;&#2482;&#2503;&#2527;&#2494;&#2480; &#2455;&#2497;&#2482;&#2507; &#2458;&#2494;&#2482;&#2494;&#2468;&#2503; &#2474;&#2494;&#2480;&#2495;?
&#2438;&#2478;&#2495; &#2441;&#2476;&#2497;&#2472;&#2509;&#2463;&#2497; 14.04 lts &#2476;&#2509;&#2479;&#2476;&#2489;&#2494;&#2480; &#2453;&#2480;&#2459;&#2495;&#2404; help me

---

### Post by Bashing-om on 2015-02-08
Ahanaf; Hi ! Welcome to the forum .

Your post did not make it. But, do I understand correctly that you are experiencing difficulties with DVDs ?
IF you have (u)buntu installed:
Have you:
```

sudo apt-get install ubuntu-restricted-extras
sudo apt-get install libdvdread4

```
Then open a terminal window and execute:
```

sudo /usr/share/doc/libdvdread4/install-css.sh

```
Rebooting may be necessary.
After this, VLC will automatically use it.
If after doing all this, you still get messages about not being able to play DVDs, check that the DVD drive has a region set.
```

sudo apt-get install libdvdcss libdvdread4 libdvdnav4

```
then again run:
```

sudo /usr/share/doc/libdvdread4/install-css.sh

```

[INDENT][INDENT]I hope this helps
[/INDENT][/INDENT]

---

