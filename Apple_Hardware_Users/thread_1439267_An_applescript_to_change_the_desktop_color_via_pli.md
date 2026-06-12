---
title: "An applescript to change the desktop color via plist edit."
date: 2010-03-26
forum: Apple Hardware Users
---

### Post by CJN on 2010-03-26
Ok, so I found this applescript somewhere, and not knowing applescript I  was wondering if someone could tell me what the edits I need to make to  duplicate the functionality found in the perl script which follows the  applescript. (ie. I want to cycle through the colors in the same  sequence)

Applescript (written by someone else for OS X)
```
tell application "System Events"
	set theDesktopPlist to property list file "~/Library/Preferences/com.apple.desktop.plist"
	set theGivenDesktop to property list item "desktopCode" of property list item "Background" of theDesktopPlist
	try
		set theColorArray to property list item "BackgroundColor" of theGivenDesktop
	on error
		set theColorArray to make new property list item at end of property list items of theGivenDesktop with properties {kind:list, name:"BackgroundColor"}
	end try
	repeat with i from 1 to 3
		if not (exists property list item i of theColorArray) then
			make new property list item at end of property list items of theColorArray with properties {kind:number, value:random number}
		else
			set value of property list item i of theColorArray to random number
		end if
	end repeat
end tell
```
 perl script (written by me for ubuntu linux)

```
#!/usr/bin/perl
my $red, $green, $blue;     
my $HEX, $stage;
$stage=1;
$red=0;
$green=0;
$blue=0;
while (1) {
#red orange yellow green blue indigo violet
if($stage==1){ #red
	if($red<255){
		$red +=1;
	}else{
		$stage=2;
	}
}elsif($stage==2){# orange, yellow
	if($green<255){
		$green +=1;
	}else{
		$stage=3;
	}
}elsif($stage==3){#green
	if($red>0){
		$red -=1;
	}else{
		$stage=4;
	}
}elsif($stage==4){#aqua
	if($blue<255){
		$blue +=1;
	}else{
		$stage=5;
	}
}elsif($stage==5){#blue
	if($green>0){
		$green -=1;
	}else{
		$stage=6;
	}
}elsif($stage==6){#indigo, violet
	if($red<255){
		$red +=1;
	}else{
		$stage=7;
	}
}elsif($stage==7){#white
	if($green<255){
		$green +=1;
	}else{
		$stage=8;
	}
}elsif($stage==8){
	if($red>0){
		$red-=1;
		$green-=1;
		$blue-=1;
	}else{
		$stage=1;
	}
}
    # convert to hex
    $HEX = sprintf("%02X%02X%02X", $red, $green, $blue);
    # set the color
    system("gconftool-2 -t str --set /desktop/gnome/background/primary_color '#$HEX'");
    sleep 1; # Update 60 times per minute
}
done
```

---

### Post by CJN on 2010-03-26
I've updated what I'm working with to the following, any advice would be welcome.

```
#!/usr/bin/osascript
on run
    tell application "System Events"
        set theDesktopPlist to property list file "~/Library/Preferences/com.apple.desktop.plist"
        set theGivenDesktop to property list item "desktopCode" of property list item "Background" of theDesktopPlist
        try
            set theColorArray to property list item "BackgroundColor" of theGivenDesktop
        on error
            set theColorArray to make new property list item at end of property list items of theGivenDesktop with properties {kind:list, name:"BackgroundColor"}
        end try
        set theRedValue to 0
        set theGreenValue to 0
        set theBlueVlaue to 0
        set theStage to 1
        repeat
            if theStage is 1 then --red
                if theRedValue is less than 255 then
                    increment theRedValue
                else
                    set theStage to 2
                end if
            else if theStage is 2 then --orange, yellow
                if theGreenValue is less than 255 then
                    increment theGreenValue
                else
                    set theStage to 3
                end if
            else if theStage is 3 then --green
                if theRedValue is greater than 0 then
                    decrement theRedValue
                else
                    set theStage to 4
                end if
            else if theStage is 4 then --aqua
                if theblue is less than 255 then
                    increment theBlueValue
                else
                    set theStage to 5
                end if
            else if theStage is 5 then --blue
                if thegreen is greater than 0 then
                    decrement theGreenValue
                else
                    set theStage to 6
                end if
            else if theStage is 6 then --indigo, violet
                if thered is less than 255 then
                    increment theRedValue
                else
                    set theStage to 7
                end if
            else if theStage is 7 then --white
                if thegreen is less than 255 then
                    increment theGreenValue
                else
                    set theStage to 8
                end if
            else if theStage is 8 then --black
                if thered is greater than 0 then
                    decrement theRedValue
                    decrement theGreenValue
                    decrement theBlueValue
                else
                    set theStage to 1
                end if
            end if
            set value of property list item 1 of theColorArray to theRedValue
            set value of property list item 2 of theColorArray to theGreenValue
            set value of property list item 3 of theColorArray to theBlueValue
            delay 1
        end repeat
    end tell
end run

on idle
    return 1
end idle
```

---

### Post by CJN on 2010-03-27
Ok so this "works" as in it changes the plist values at the right rate and to the right values, but the desktop doesn't update when the plist is changed, so what can I do to get that last bit working?
```

#!/usr/bin/osascript
tell application "System Events"
    set theDesktopPlist to property list file "~/Library/Preferences/com.apple.desktop.plist"
    set theGivenDesktop to property list item "desktopCode" of property list item "Background" of theDesktopPlist
    try
        set theColorArray to property list item "BackgroundColor" of theGivenDesktop
    on error
        set theColorArray to make new property list item at end of property list items of theGivenDesktop with properties {kind:list, name:"BackgroundColor"}
    end try
    set theRedValue to 0
    set theGreenValue to 0
    set theBlueValue to 0
    set theStage to 1
    repeat
        if theStage is 1 then --red
            if theRedValue is less than 1 then
                set theRedValue to theRedValue + 0.004
            else
                set theStage to 2
            end if
        else if theStage is 2 then --orange, yellow
            if theGreenValue is less than 1 then
                set theGreenValue to theGreenValue + 0.004
            else
                set theStage to 3
            end if
        else if theStage is 3 then --green
            if theRedValue is greater than 0 then
                set theRedValue to theRedValue - 0.004
            else
                set theStage to 4
            end if
        else if theStage is 4 then --aqua
            if theblue is less than 1 then
                set theBlueValue to theBlueValue + 0.004
            else
                set theStage to 5
            end if
        else if theStage is 5 then --blue
            if thegreen is greater than 0 then
                set theGreenValue to theGreenValue - 0.004
            else
                set theStage to 6
            end if
        else if theStage is 6 then --indigo, violet
            if thered is less than 1 then
                set theRedValue to theRedValue + 0.004
            else
                set theStage to 7
            end if
        else if theStage is 7 then --white
            if thegreen is less than 1 then
                set theGreenValue to theGreenValue + 0.004
            else
                set theStage to 8
            end if
        else if theStage is 8 then --black
            if thered is greater than 0 then
                set theRedValue to theRedValue - 0.004
                set theGreenValue to theGreenValue - 0.004
                set theBlueValue to theBlueValue - 0.004
            else
                set theStage to 1
            end if
        end if
        set value of property list item 1 of theColorArray to theRedValue
        set value of property list item 2 of theColorArray to theGreenValue
        set value of property list item 3 of theColorArray to theBlueValue
        delay 1
    end repeat
end tell
```

---

