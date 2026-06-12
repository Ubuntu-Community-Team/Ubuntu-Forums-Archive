---
title: "Need OnScreen Bangla Keyboard"
date: 2018-08-06
forum: Bangladesh Team
---

### Post by arifdkbd on 2018-08-06
I just switched from WIN 10 to Ubuntu 18.04.1, on WIN 10 I can use onscreen Bangla keyboard for Bangla typing.
Now in Ubuntu, I want to type Bangla using onscreen Bangla keyboard.
Can you pls suggest me which will be the best onscreen keyboard for Ubuntu?

---

### Post by pavlushka on 2018-10-06
"Onboard" on screen keyboard available in Ubuntu software repository and you might need "ibus-m17n" installed along with. Ibus will give you Bengali writing capacity and Onboard will give you on screen writing capacity.

---

### Post by fojrex on 2018-10-30
&#2438;&#2474;&#2472;&#2495; &#2438;&#2439;&#2476;&#2494;&#2488; &#2437;&#2477;&#2509;&#2480; &#2476;&#2509;&#2479;&#2476;&#2489;&#2494;&#2480; &#2453;&#2480;&#2468;&#2503; &#2474;&#2494;&#2480;&#2503;&#2472; &#2437;&#2469;&#2476;&#2494; &#2472;&#2495;&#2458;&#2503;&#2480; &#2482;&#2495;&#2434;&#2453; &#2469;&#2503;&#2453;&#2503; &#2465;&#2494;&#2441;&#2472;&#2482;&#2507;&#2465; &#2453;&#2480;&#2503; &#2458;&#2494;&#2482;&#2494;&#2468;&#2503; &#2474;&#2494;&#2480;&#2503;&#2472;, &#2468;&#2476;&#2503; &#2437;&#2476;&#2486;&#2509;&#2479;&#2439; Wine &#2439;&#2472;&#2509;&#2488;&#2463;&#2482; &#2453;&#2480;&#2494; &#2469;&#2494;&#2453;&#2468;&#2503; &#2489;&#2476;&#2503; , &#2472;&#2494; &#2489;&#2482;&#2503; &#2476;&#2509;&#2479;&#2476;&#2489;&#2494;&#2480; &#2453;&#2480;&#2468;&#2503; &#2474;&#2494;&#2480;&#2476;&#2503;&#2472; &#2472;&#2494;&#2404; [https://sourceforge.net/projects/on-screen-bangla-keyboard/](https://sourceforge.net/projects/on-screen-bangla-keyboard/)

---

### Post by ahmedomar on 2019-03-25
[U][B]step1.Getting A Onscreen Keyboard:
[/B][/U]
**1**.Ubuntu comes with a onscreen keyboard by default it is called "OnBoard" which you can find in app menu.

**2**.In case "OnBoard" is not installed then open a terminal with (ctrl+alt+t)

**3**.In the terminal window type: sudo apt install onboard

**4**.As "OnBoard" is installed open it from app menu and boom you get a onscreen keyboard.

**5**.There is a icon on the task bar which you can use to enable and disable the keyboard.

*Now to type Bengali with it follow the next instruction. we will be installing avro now.*


[B]_step2.Getting Bengali Typing feature:_

[/B]**1**.install ibus with (sudo apt install ibus)

**2**.download this file: [https://github.com/maateen/avro/releases/download/v2.1/avro_2.1-3_all.deb](https://github.com/maateen/avro/releases/download/v2.1/avro_2.1-3_all.deb)   (can check for any latest version if you want)

**3**.go to the folder where you downloaded the file

**4**.right click on any blank space and select "open terminal here" from drop down menu.

**5**.In the termial window type: sudo dpkg -i avro_2.1-3_all.deb

**6**.from menu goto IBus Preferences >> add >> Bengali >> Avro Phonetic or whatever there is.... and apply

**7**.Notice that a new icon showed upon the right of your bar or task bar (basically the icon is a keyboard picture or it says EN)

**8**.click that icon and select avro. if avro is not there goto step 6 and check you did it right or not.

**9**.The icon should turn avro orange and you can type bangla with phonectics on any place like google, facebook etc

**10**.To change to english just click that previous icon(which now shows avro) and select english


Hope it fits your needs

---

