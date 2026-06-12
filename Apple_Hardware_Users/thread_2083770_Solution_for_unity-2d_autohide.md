---
title: "Solution for unity-2d autohide"
date: 2012-11-13
forum: Apple Hardware Users
---

### Post by rsavage on 2012-11-13
I've been looking again at unity-2d and thought I'd share a solution to bug [https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/989477](https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/989477) 

Type the command
```

gksudo gedit /usr/share/unity-2d/shell/Shell.qml

```

Scroll down to this bit:
```

    PointerBarrier {
        property int x: declarativeView.globalPosition.x + (Utils.isLeftToRight() ? 0 : shell.width)
        property bool enableTrigger: launcherLoader.launcherInHideMode && launcherLoader.loadLauncher
        // This enableSticky logic has a 'bug' int RTL where the right most screen will still have enableSticky
        // set to true, but it won't cause any issue other than consuming a few bytes of mememory and calculating the 
        // rightmost x is probably more expensive and error prone than just enabling the extra barrier
        property bool enableSticky: unity2dConfiguration.stickyEdges && declarativeView.screen.geometry.x > 0

        id: leftBarrier
        triggerDirection: Utils.isLeftToRight() ? PointerBarrier.TriggerFromRight : PointerBarrier.TriggerFromLeft
        triggerZoneEnabled: enableTrigger && !launcherLoader.visibilityController.shown
        triggerOnly: enableTrigger && !enableSticky
        p1: Qt.point(x, declarativeView.screen.geometry.y)
        p2: Qt.point(x, declarativeView.screen.geometry.y + declarativeView.screen.geometry.height)
        triggerZoneP1: Qt.point(x, launcher2dConfiguration.revealMode == 1 ? declarativeView.screen.geometry.y : declarativeView.globalPosition.y)
        triggerZoneP2: Qt.point(x, launcher2dConfiguration.revealMode == 1 ? declarativeView.screen.geometry.y + 1 : declarativeView.globalPosition.y + launcherLoader.height)
        threshold: (enableSticky || enableTrigger) ? launcher2dConfiguration.edgeStopVelocity : -1
        maxVelocityMultiplier: launcher2dConfiguration.edgeResponsiveness
        decayRate: 1500
        triggerPressure: launcher2dConfiguration.edgeRevealPressure
        breakPressure: 2000

        onTriggered: launcherLoader.item.barrierTriggered()
    }

```

Change the decayRate and breakPressure to the values above.

Logout and log back in.

---

### Post by rsavage on 2012-11-13
Continuing the theme of hacks....

If you want to start the dash from the command line, you can use this command in 12.04:

```

dbus-send --type=method_call --dest=com.canonical.Unity2d.Shell /Dash com.canonical.Unity2d.Dash.activateHome

```

---

### Post by heliboy on 2013-01-02
Thanks!  Worked for me on 12.04 and a G4 "iLamp" iMac powerpc.  Tried many other approaches, and this is the only one that did the trick.  Thanks again.

---

