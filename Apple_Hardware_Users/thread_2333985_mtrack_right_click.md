---
title: "mtrack right click"
date: 2016-08-15
forum: Apple Hardware Users
---

### Post by AzrinArius on 2016-08-15
Hi,

I just installed Ubuntu on an old MacBook(mid-2010). The trackpad was a pain so I searched around and found out about mtrack. I have it installed and have it configured so it works how I want. However, I have no right click capabilities and I can't figure out how to set that up. I've tried googling but it seems largely about double-clicking for right or using two fingers. What I want is the bottom right corner of the trackpad to act as a right click on click( or tap ).

The problem is I don't really know what the options in the configuration file mean. I've just been trial/erroring. Again, googling for that information just results in a lot of threads from different forums where people have posted their configs.

Can anybody help, or point me in the direction of a list of the options with an explanation?

Here's my current config.

```



MatchIsTouchpad "on"




       Identifier      "Touchpads"
        Driver          "mtrack"
        Option          "Sensitivity" "0.55"
        Option          "FingerHigh" "12"
        Option          "FingerLow" "1"
        Option          "IgnoreThumb" "true"
        Option          "IgnorePalm" "true"
        Option          "TapButton1" "1"
        Option          "TapButton2" "0"
        Option          "TapButton3" "0"
        Option          "TapButton4" "0"
        Option          "ClickFinger1" "1"
        Option          "ClickFinger2" "3"
        Option          "ClickFinger3" "3"
        Option          "ButtonMoveEmulate" "false"
        Option          "ButtonIntegrated" "true"
        Option          "ClickTime" "25"
        Option          "BottomEdge" "25"
        Option          "SwipeLeftButton" "8"
        Option          "SwipeRightButton" "9"
        Option          "SwipeUpButton" "0"
        Option          "SwipeDownButton" "0"
        Option          "ScrollDistance" "75"
        Option          "ScrollUpButton" "5"
Option          "ScrollDownButton" "4"
Option "AccelerationProfile" "1"
Option "ConstantDeceleration" "2.0"
Option "AdaptiveDeceleration" "2.0"

```

Thanks for any help.

---

### Post by howefield on 2016-08-15
Thread moved to the "*Apple Hardware Users*" forum for a better fit.

---

