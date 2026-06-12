---
title: "Sensitive TrackPad on MacBook 1,1"
date: 2010-12-04
forum: Apple Hardware Users
---

### Post by jgould81 on 2010-12-04
The situation: I have a MacBook 1,1 (Early 2006) Model that I've installed Lucid on (10.04 XUbuntu.) The trackpad responds to every single bump, tap, etc.  I tried adding the file /etc/hal/policy/appletouch ```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
   <merge key="input.x11_options.Device" type="string">/dev/psaux</merge>
   <merge key="input.x11_options.Protocol" type="string">auto-dev</merge>
   <merge key="input.x11_options.SHMConfig" type="string">true</merge>
   <merge key="input.x11_options.LeftEdge" type="string">10</merge>
   <merge key="input.x11_options.RightEdge" type="string">1200</merge>
   <merge key="input.x11_options.TopEdge" type="string">10</merge>
   <merge key="input.x11_options.BottomEdge" type="string">370</merge>
   <merge key="input.x11_options.FingerLow" type="string">10</merge>
   <merge key="input.x11_options.FingerHigh" type="string">20</merge>
   <merge key="input.x11_options.MaxTapTime" type="string">180</merge>
   <merge key="input.x11_options.MaxTapMove" type="string">220</merge>
   <merge key="input.x11_options.SingleTapTimeout" type="string">100</merge>
   <merge key="input.x11_options.MaxDoubleTapTime" type="string">180</merge>
   <merge key="input.x11_options.LockedDrags" type="string">off</merge>
   <merge key="input.x11_options.MinSpeed" type="string">1.10</merge>
   <merge key="input.x11_options.MaxSpeed" type="string">1.30</merge>
   <merge key="input.x11_options.AccelFactor" type="string">0.08</merge>
   <merge key="input.x11_options.TapButton1" type="string">1</merge>
   <merge key="input.x11_options.TapButton2" type="string">3</merge>
   <merge key="input.x11_options.TapButton3" type="string">2</merge>
   <merge key="input.x11_options.RTCornerButton" type="string">0</merge>
   <merge key="input.x11_options.RBCornerButton" type="string">0</merge>
   <merge key="input.x11_options.LTCornerButton" type="string">0</merge>
   <merge key="input.x11_options.LBCornerButton" type="string">0</merge>
   <merge key="input.x11_options.VertScrollDelta" type="string">20</merge>
   <merge key="input.x11_options.HorizScrollDelta" type="string">50</merge>
   <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>
   <merge key="input.x11_options.HorizEdgeScroll" type="string">0</merge>
   <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
   <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
  </match> 
 </device>
</deviceinfo>
```

I had migrated back to the Mac OS after a brief stint with 9.04 and now have no clue how I fixed this or if I ever fixed it.  I have even tried the updated (I think) synaptics driver from the MacTel PPA, Netiher thing I've tried had any affect on this. 

I'm at a loss and about to reinstall Snow Leopard....

---

