---
title: "Help with quickcam communicate stx"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by gerald paster on 2008-04-10
Hi to everybody.I am new to linux and new to this site. I have a toshiba laptop in which i installed gutsy gibbon. it works fine. i purchased a webcam to use it for skype.(after some research, i found out that quickcam communicate stx by logitech should work out of the box). After connecting the camera to the usb port nothing happened. the cd that comes with the camera is not working in linux.Please provide me with step by step guidance since i am new with linux and especially with webcams. Thanks.

---

### Post by herbster on 2008-04-10
The CD that comes with your webcam is not designed for linux, it is Windows software.

Your device most likely does work, you can find out by unplugging it and plugging it back in, and immediately looking at the dmesg output. Open a terminal (Applications  > Accessories > Terminal) and paste the output you get when you type this command and hit ENTER:

```
dmesg
```

Paste the output in a post here using the [code] tags in your post.

---

### Post by gerald paster on 2008-04-10
current] 
[135029.680000] : Add. Sense: Medium not present
[135029.680000] end_request: I/O error, dev sr0, sector 5491560
[135029.684000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.684000] : Add. Sense: Medium not present
[135029.684000] end_request: I/O error, dev sr0, sector 5491564
[135029.684000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.684000] : Add. Sense: Medium not present
[135029.684000] end_request: I/O error, dev sr0, sector 5491560
[135029.688000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.688000] : Add. Sense: Medium not present
[135029.688000] end_request: I/O error, dev sr0, sector 5491564
[135029.688000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.688000] : Add. Sense: Medium not present
[135029.688000] end_request: I/O error, dev sr0, sector 5491568
[135029.688000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.688000] : Add. Sense: Medium not present
[135029.688000] end_request: I/O error, dev sr0, sector 5491572
[135029.692000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.692000] : Add. Sense: Medium not present
[135029.692000] end_request: I/O error, dev sr0, sector 5491568
[135029.692000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.692000] : Add. Sense: Medium not present
[135029.692000] end_request: I/O error, dev sr0, sector 5491572
[135029.696000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.696000] : Add. Sense: Medium not present
[135029.696000] end_request: I/O error, dev sr0, sector 5491576
[135029.696000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.696000] : Add. Sense: Medium not present
[135029.696000] end_request: I/O error, dev sr0, sector 5491580
[135029.696000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.696000] : Add. Sense: Medium not present
[135029.696000] end_request: I/O error, dev sr0, sector 5491576
[135029.700000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.700000] : Add. Sense: Medium not present
[135029.700000] end_request: I/O error, dev sr0, sector 5491580
[135029.700000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.700000] : Add. Sense: Medium not present
[135029.700000] end_request: I/O error, dev sr0, sector 5491584
[135029.704000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.704000] : Add. Sense: Medium not present
[135029.704000] end_request: I/O error, dev sr0, sector 5491588
[135029.704000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.704000] : Add. Sense: Medium not present
[135029.704000] end_request: I/O error, dev sr0, sector 5491584
[135029.704000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.704000] : Add. Sense: Medium not present
[135029.704000] end_request: I/O error, dev sr0, sector 5491588
[135029.708000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.708000] : Add. Sense: Medium not present
[135029.708000] end_request: I/O error, dev sr0, sector 5491592
[135029.708000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.708000] : Add. Sense: Medium not present
[135029.708000] end_request: I/O error, dev sr0, sector 5491596
[135029.712000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.712000] : Add. Sense: Medium not present
[135029.712000] end_request: I/O error, dev sr0, sector 5491592
[135029.712000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.712000] : Add. Sense: Medium not present
[135029.712000] end_request: I/O error, dev sr0, sector 5491596
[135029.712000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.712000] : Add. Sense: Medium not present
[135029.712000] end_request: I/O error, dev sr0, sector 5491600
[135029.716000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.716000] : Add. Sense: Medium not present
[135029.716000] end_request: I/O error, dev sr0, sector 5491604
[135029.716000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.716000] : Add. Sense: Medium not present
[135029.716000] end_request: I/O error, dev sr0, sector 5491600
[135029.720000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.720000] : Add. Sense: Medium not present
[135029.720000] end_request: I/O error, dev sr0, sector 5491604
[135029.720000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.720000] : Add. Sense: Medium not present
[135029.720000] end_request: I/O error, dev sr0, sector 5491608
[135029.720000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.720000] : Add. Sense: Medium not present
[135029.720000] end_request: I/O error, dev sr0, sector 5491612
[135029.724000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.724000] : Add. Sense: Medium not present
[135029.724000] end_request: I/O error, dev sr0, sector 5491608
[135029.724000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.724000] : Add. Sense: Medium not present
[135029.724000] end_request: I/O error, dev sr0, sector 5491612
[135029.728000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.728000] : Add. Sense: Medium not present
[135029.728000] end_request: I/O error, dev sr0, sector 5491616
[135029.728000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.728000] : Add. Sense: Medium not present
[135029.728000] end_request: I/O error, dev sr0, sector 5491620
[135029.728000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.728000] : Add. Sense: Medium not present
[135029.728000] end_request: I/O error, dev sr0, sector 5491616
[135029.732000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.732000] : Add. Sense: Medium not present
[135029.732000] end_request: I/O error, dev sr0, sector 5491620
[135029.732000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.732000] : Add. Sense: Medium not present
[135029.732000] end_request: I/O error, dev sr0, sector 5491624
[135029.736000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.736000] : Add. Sense: Medium not present
[135029.736000] end_request: I/O error, dev sr0, sector 5491628
[135029.736000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.736000] : Add. Sense: Medium not present
[135029.736000] end_request: I/O error, dev sr0, sector 5491624
[135029.736000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.736000] : Add. Sense: Medium not present
[135029.736000] end_request: I/O error, dev sr0, sector 5491628
[135029.740000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.740000] : Add. Sense: Medium not present
[135029.740000] end_request: I/O error, dev sr0, sector 5491632
[135029.740000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.740000] : Add. Sense: Medium not present
[135029.740000] end_request: I/O error, dev sr0, sector 5491636
[135029.744000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.744000] : Add. Sense: Medium not present
[135029.744000] end_request: I/O error, dev sr0, sector 5491632
[135029.744000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.744000] : Add. Sense: Medium not present
[135029.744000] end_request: I/O error, dev sr0, sector 5491636
[135029.744000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.744000] : Add. Sense: Medium not present
[135029.744000] end_request: I/O error, dev sr0, sector 5491640
[135029.748000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.748000] : Add. Sense: Medium not present
[135029.748000] end_request: I/O error, dev sr0, sector 5491644
[135029.748000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.748000] : Add. Sense: Medium not present
[135029.748000] end_request: I/O error, dev sr0, sector 5491640
[135029.752000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.752000] : Add. Sense: Medium not present
[135029.752000] end_request: I/O error, dev sr0, sector 5491644
[135029.752000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.752000] : Add. Sense: Medium not present
[135029.752000] end_request: I/O error, dev sr0, sector 5491648
[135029.752000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.752000] : Add. Sense: Medium not present
[135029.752000] end_request: I/O error, dev sr0, sector 5491652
[135029.756000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.756000] : Add. Sense: Medium not present
[135029.756000] end_request: I/O error, dev sr0, sector 5491648
[135029.756000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.756000] : Add. Sense: Medium not present
[135029.756000] end_request: I/O error, dev sr0, sector 5491652
[135029.760000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.760000] : Add. Sense: Medium not present
[135029.760000] end_request: I/O error, dev sr0, sector 5491656
[135029.764000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.764000] : Add. Sense: Medium not present
[135029.764000] end_request: I/O error, dev sr0, sector 5491660
[135029.764000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.764000] : Add. Sense: Medium not present
[135029.764000] end_request: I/O error, dev sr0, sector 5491656
[135029.764000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.764000] : Add. Sense: Medium not present
[135029.764000] end_request: I/O error, dev sr0, sector 5491660
[135029.768000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.768000] : Add. Sense: Medium not present
[135029.768000] end_request: I/O error, dev sr0, sector 5491664
[135029.768000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.768000] : Add. Sense: Medium not present
[135029.768000] end_request: I/O error, dev sr0, sector 5491668
[135029.772000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.772000] : Add. Sense: Medium not present
[135029.772000] end_request: I/O error, dev sr0, sector 5491664
[135029.772000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.772000] : Add. Sense: Medium not present
[135029.772000] end_request: I/O error, dev sr0, sector 5491668
[135029.772000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.772000] : Add. Sense: Medium not present
[135029.772000] end_request: I/O error, dev sr0, sector 5491672
[135029.776000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.776000] : Add. Sense: Medium not present
[135029.776000] end_request: I/O error, dev sr0, sector 5491676
[135029.776000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.776000] : Add. Sense: Medium not present
[135029.776000] end_request: I/O error, dev sr0, sector 5491672
[135029.780000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.780000] : Add. Sense: Medium not present
[135029.780000] end_request: I/O error, dev sr0, sector 5491676
[135029.780000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.780000] : Add. Sense: Medium not present
[135029.780000] end_request: I/O error, dev sr0, sector 5491680
[135029.780000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.780000] : Add. Sense: Medium not present
[135029.780000] end_request: I/O error, dev sr0, sector 5491684
[135029.784000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.784000] : Add. Sense: Medium not present
[135029.784000] end_request: I/O error, dev sr0, sector 5491680
[135029.784000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.784000] : Add. Sense: Medium not present
[135029.784000] end_request: I/O error, dev sr0, sector 5491684
[135029.784000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.784000] : Add. Sense: Medium not present
[135029.784000] end_request: I/O error, dev sr0, sector 5491688
[135029.788000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.788000] : Add. Sense: Medium not present
[135029.788000] end_request: I/O error, dev sr0, sector 5491692
[135029.788000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.788000] : Add. Sense: Medium not present
[135029.788000] end_request: I/O error, dev sr0, sector 5491688
[135029.792000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.792000] : Add. Sense: Medium not present
[135029.792000] end_request: I/O error, dev sr0, sector 5491692
[135029.792000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.792000] : Add. Sense: Medium not present
[135029.792000] end_request: I/O error, dev sr0, sector 5491696
[135029.792000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.792000] : Add. Sense: Medium not present
[135029.792000] end_request: I/O error, dev sr0, sector 5491700
[135029.796000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.796000] : Add. Sense: Medium not present
[135029.796000] end_request: I/O error, dev sr0, sector 5491696
[135029.796000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.796000] : Add. Sense: Medium not present
[135029.796000] end_request: I/O error, dev sr0, sector 5491700
[135029.800000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.800000] : Add. Sense: Medium not present
[135029.800000] end_request: I/O error, dev sr0, sector 5491704
[135029.800000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.800000] : Add. Sense: Medium not present
[135029.800000] end_request: I/O error, dev sr0, sector 5491708
[135029.800000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.800000] : Add. Sense: Medium not present
[135029.800000] end_request: I/O error, dev sr0, sector 5491704
[135029.804000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.804000] : Add. Sense: Medium not present
[135029.804000] end_request: I/O error, dev sr0, sector 5491708
[135029.804000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.804000] : Add. Sense: Medium not present
[135029.804000] end_request: I/O error, dev sr0, sector 5491712
[135029.808000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.808000] : Add. Sense: Medium not present
[135029.808000] end_request: I/O error, dev sr0, sector 5491716
[135029.808000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.808000] : Add. Sense: Medium not present
[135029.808000] end_request: I/O error, dev sr0, sector 5491712
[135029.808000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.808000] : Add. Sense: Medium not present
[135029.808000] end_request: I/O error, dev sr0, sector 5491716
[135029.816000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.816000] : Add. Sense: Medium not present
[135029.816000] end_request: I/O error, dev sr0, sector 5491720
[135029.820000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.820000] : Add. Sense: Medium not present
[135029.820000] end_request: I/O error, dev sr0, sector 5491724
[135029.820000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.820000] : Add. Sense: Medium not present
[135029.820000] end_request: I/O error, dev sr0, sector 5491720
[135029.824000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.824000] : Add. Sense: Medium not present
[135029.824000] end_request: I/O error, dev sr0, sector 5491724
[135029.824000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.824000] : Add. Sense: Medium not present
[135029.824000] end_request: I/O error, dev sr0, sector 5491728
[135029.824000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.824000] : Add. Sense: Medium not present
[135029.824000] end_request: I/O error, dev sr0, sector 5491728
[135029.828000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.828000] : Add. Sense: Medium not present
[135029.828000] end_request: I/O error, dev sr0, sector 5491732
[135029.828000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.828000] : Add. Sense: Medium not present
[135029.828000] end_request: I/O error, dev sr0, sector 5491736
[135029.832000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.832000] : Add. Sense: Medium not present
[135029.832000] end_request: I/O error, dev sr0, sector 5491740
[135029.832000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.832000] : Add. Sense: Medium not present
[135029.832000] end_request: I/O error, dev sr0, sector 5491736
[135029.832000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.832000] : Add. Sense: Medium not present
[135029.832000] end_request: I/O error, dev sr0, sector 5491740
[135029.836000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.836000] : Add. Sense: Medium not present
[135029.836000] end_request: I/O error, dev sr0, sector 5491744
[135029.836000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.836000] : Add. Sense: Medium not present
[135029.836000] end_request: I/O error, dev sr0, sector 5491748
[135029.840000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.840000] : Add. Sense: Medium not present
[135029.840000] end_request: I/O error, dev sr0, sector 5491744
[135029.840000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.840000] : Add. Sense: Medium not present
[135029.840000] end_request: I/O error, dev sr0, sector 5491748
[135029.844000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.844000] : Add. Sense: Medium not present
[135029.844000] end_request: I/O error, dev sr0, sector 5491752
[135029.844000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.844000] : Add. Sense: Medium not present
[135029.844000] end_request: I/O error, dev sr0, sector 5491756
[135029.848000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.848000] : Add. Sense: Medium not present
[135029.848000] end_request: I/O error, dev sr0, sector 5491752
[135029.848000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.848000] : Add. Sense: Medium not present
[135029.848000] end_request: I/O error, dev sr0, sector 5491756
[135029.848000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.848000] : Add. Sense: Medium not present
[135029.848000] end_request: I/O error, dev sr0, sector 5491760
[135029.852000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.852000] : Add. Sense: Medium not present
[135029.852000] end_request: I/O error, dev sr0, sector 5491764
[135029.852000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.852000] : Add. Sense: Medium not present
[135029.852000] end_request: I/O error, dev sr0, sector 5491760
[135029.856000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.856000] : Add. Sense: Medium not present
[135029.856000] end_request: I/O error, dev sr0, sector 5491764
[135029.856000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.856000] : Add. Sense: Medium not present
[135029.856000] end_request: I/O error, dev sr0, sector 5491768
[135029.856000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.856000] : Add. Sense: Medium not present
[135029.856000] end_request: I/O error, dev sr0, sector 5491772
[135029.860000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.860000] : Add. Sense: Medium not present
[135029.860000] end_request: I/O error, dev sr0, sector 5491768
[135029.860000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.860000] : Add. Sense: Medium not present
[135029.860000] end_request: I/O error, dev sr0, sector 5491772
[135029.864000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.864000] : Add. Sense: Medium not present
[135029.864000] end_request: I/O error, dev sr0, sector 5491776
[135029.864000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.864000] : Add. Sense: Medium not present
[135029.864000] end_request: I/O error, dev sr0, sector 5491780
[135029.864000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.864000] : Add. Sense: Medium not present
[135029.864000] end_request: I/O error, dev sr0, sector 5491776
[135029.868000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.868000] : Add. Sense: Medium not present
[135029.868000] end_request: I/O error, dev sr0, sector 5491780
[135029.868000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.868000] : Add. Sense: Medium not present
[135029.868000] end_request: I/O error, dev sr0, sector 5491784
[135029.872000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.872000] : Add. Sense: Medium not present
[135029.872000] end_request: I/O error, dev sr0, sector 5491788
[135029.872000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.872000] : Add. Sense: Medium not present
[135029.872000] end_request: I/O error, dev sr0, sector 5491784
[135029.876000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.876000] : Add. Sense: Medium not present
[135029.876000] end_request: I/O error, dev sr0, sector 5491788
[135029.876000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.876000] : Add. Sense: Medium not present
[135029.876000] end_request: I/O error, dev sr0, sector 5491792
[135029.876000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.876000] : Add. Sense: Medium not present
[135029.876000] end_request: I/O error, dev sr0, sector 5491796
[135029.880000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.880000] : Add. Sense: Medium not present
[135029.880000] end_request: I/O error, dev sr0, sector 5491792
[135029.880000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.880000] : Add. Sense: Medium not present
[135029.880000] end_request: I/O error, dev sr0, sector 5491796
[135029.880000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.880000] : Add. Sense: Medium not present
[135029.880000] end_request: I/O error, dev sr0, sector 5491800
[135029.884000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.884000] : Add. Sense: Medium not present
[135029.884000] end_request: I/O error, dev sr0, sector 5491804
[135029.884000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.884000] : Add. Sense: Medium not present
[135029.884000] end_request: I/O error, dev sr0, sector 5491800
[135029.888000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.888000] : Add. Sense: Medium not present
[135029.888000] end_request: I/O error, dev sr0, sector 5491804
[135029.888000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.888000] : Add. Sense: Medium not present
[135029.888000] end_request: I/O error, dev sr0, sector 5491808
[135029.888000] sr 1:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[135029.888000] : Add. Sense: Medium not present
[135029.888000] end_request: I/O error, dev sr0, sector 5491812

---

### Post by herbster on 2008-04-10
Your CD/DVD drive is messed up it seems, or some operation is not responding correctly-- perhaps nautilus.

Does your CD/DVD drive work properly? Can you copy files from CD/DVD > disk?

There's no visible output for your webcam, unless it is sr0, and I'm pretty sure that address is a cd/dvd drive.

---

### Post by gerald paster on 2008-04-11
You were right. If I click on CD/DVD Creator "write to disc" is frozen. If I click on "Audio disc" in the side pan, I get the following warning: "cdda:///dev/scd0" is not a valid location. Any ideas how to fix that? Thanks

---

### Post by herbster on 2008-04-11
Paste the contents of your fstab file:

```
cat /etc/fstab
```

Also, pop in a data CD and go to Places > Computer, double-click the cd drive and see if it displays, or gives you an error of any sort. If you can see the files on your cd, try copying a few over to your Desktop or somewhere temporarily just to test its functionality.

---

### Post by gerald paster on 2008-04-12
if i type the code: cat/etc/fstab in the terminal, i get: bash: cat/etc/fstab: No such file or directory. Still need help. Thanks

---

### Post by herbster on 2008-04-12
You didn't put a space in between "cat" and "/etc/fstab".

---

### Post by gerald paster on 2008-04-14
With code: cat /etc/fstab , that's what i see:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c857e243-2331-46bd-a347-694c62206881 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e52bc66a-7a04-4413-8e9b-6f7a9b54b1a0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
Still confused.Thanks

---

### Post by zepto on 2008-04-15
Hello! You may check this site to make your webcam work. [http://openfacts.berlios.de/index-en.phtml?title=Linux_UVC](http://openfacts.berlios.de/index-en.phtml?title=Linux_UVC)

After compiling it should work. My Logitech 9000 did anyway. Also grab the viewer, or another program called Cheese.

---

### Post by gerald paster on 2008-04-18
i reinstalled ubuntu gutsy gibbon. i can't see any movie on dvd. it keeps telling me
totem could not play 'dvd://media/cdrom0'   There is no plugin to handle this movie. 
Probably this is the reason why my webcam is not working at all. Please help. Thanks

---

