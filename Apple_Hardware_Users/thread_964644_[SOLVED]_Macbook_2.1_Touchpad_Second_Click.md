---
title: "[SOLVED] Macbook 2.1 Touchpad Second Click"
date: 2008-10-31
forum: Apple Hardware Users
---

### Post by kestaz on 2008-10-31
I am using Ubuntu 8.10 latest version. I searched Ubuntu Wiki how to configure touchpad. I made configuration in /etc/hal/fdi/policy folder:

kestaz@macbook:/etc/hal/fdi/policy$ cat tesd.fdi 
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <match key="info.product" contains="appletouch">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.SHMConfig" type="string">true</merge>
        <merge key="input.x11_options.LeftEdge" type="string">150</merge>
	<merge key="input.x11_options.RightEdge" type="string">1070</merge>
	<merge key="input.x11_options.TopEdge" type="string">100</merge>
	<merge key="input.x11_options.BottomEdge" type="string">310</merge>
	<merge key="input.x11_options.FingerLow" type="string">25</merge>
	<merge key="input.x11_options.FingerHigh" type="string">30</merge>
	<merge key="input.x11_options.MaxTimeTap" type="string">180</merge>
	<merge key="input.x11_options.MaxTimeMove" type="string">220</merge>
	<merge key="input.x11_options.MaxDoubleTapTime" type="string">180</merge>
	<merge key="input.x11_options.LockedDrags" type="string">off</merge>
	<merge key="input.x11_options.MinSpeed" type="string">1.10</merge>
	<merge key="input.x11_options.MaxSpeed" type="string">1.30</merge>
	<merge key="input.x11_options.AccelFactor" type="string">0.08</merge>
	<merge key="input.x11_options.VertEdgeScroll" type="string">false</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">false</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">false</merge>
	<merge key="input.x11_options.VertScrollDelta" type="string">20</merge>
	<merge key="input.x11_options.HorizScrollDelta" type="string">50</merge>
        <merge key="input.x11_options.RTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.RBCornerButton" type="string">3</merge>
        <merge key="input.x11_options.LBCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.TapButton1" type="string">0</merge>
        <merge key="input.x11_options.TapButton2" type="string">0</merge>
        <merge key="input.x11_options.TapButton3" type="string">0</merge>
        <merge key="input.x11_options.PalmDetect" type="string">1</merge>
      </match>
    </match>
  </device>
</deviceinfo>

Everything works.. except RBCornerButton. Any ones knows how to fix this problem ?
Actually can i donwload better driver from mactel-support ?

---

### Post by kestaz on 2008-10-31
ahh, this configuration soddenly started working. Hope this configuration helps somebody. I coped this from ubuntu wiki ..

---

### Post by kosumi68 on 2008-10-31
Would you please switch the status of the thread to solved? It makes a big difference to people browsing the threads.

Thanks!

---

### Post by cvasilak on 2008-11-02
Hi there,

For users adding the previous configuration stated by the user and realize that tapping and right click(with both two fingers) on the touchpad doesn't work you can try the following configuration. In my MacBook Pro 2.1 the synaptics touchpad now works fluently.


Note the difference is that we added some more keys to initialize the tap and the right click.

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
<device>
<match key="info.capabilities" contains="input.touchpad">
<match key="info.product" contains="appletouch">
<merge key="input.x11_driver" type="string">synaptics</merge>
<merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
<merge key="input.x11_options.SHMConfig" type="string">true</merge>
<merge key="input.x11_options.LeftEdge" type="string">10</merge>
<merge key="input.x11_options.RightEdge" type="string">1200</merge>
<merge key="input.x11_options.TopEdge" type="string">10</merge>
<merge key="input.x11_options.BottomEdge" type="string">370</merge>
<merge key="input.x11_options.FingerLow" type="string">10</merge>
<merge key="input.x11_options.FingerHigh" type="string">20</merge>
<merge key="input.x11_options.MaxTimeTap" type="string">180</merge>
<merge key="input.x11_options.MaxTimeMove" type="string">220</merge>
<merge key="input.x11_options.SingleTapTimeout" type="string">100</merge>
<merge key="input.x11_options.MaxDoubleTapTime" type="string">180</merge>
<merge key="input.x11_options.LockedDrags" type="string">off</merge>
<merge key="input.x11_options.MinSpeed" type="string">1.10</merge>
<merge key="input.x11_options.MaxSpeed" type="string">1.30</merge>
<merge key="input.x11_options.AccelFactor" type="string">0.08</merge>
<merge key="input.x11_options.VertEdgeScroll" type="string">false</merge>
<merge key="input.x11_options.HorizEdgeScroll" type="string">false</merge>
<merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>
<merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>
<merge key="input.x11_options.VertScrollDelta" type="string">20</merge>
<merge key="input.x11_options.HorizScrollDelta" type="string">50</merge>
<merge key="input.x11_options.RTCornerButton" type="string">0</merge>
<merge key="input.x11_options.RBCornerButton" type="string">3</merge>
<merge key="input.x11_options.LBCornerButton" type="string">0</merge>
<merge key="input.x11_options.LTCornerButton" type="string">0</merge>
<merge key="input.x11_options.TapButton1" type="string">1</merge>
<merge key="input.x11_options.TapButton2" type="string">3</merge>
<merge key="input.x11_options.TapButton3" type="string">2</merge>
</match>
</match>
</device>
</deviceinfo>


Regards,
Christos

---

