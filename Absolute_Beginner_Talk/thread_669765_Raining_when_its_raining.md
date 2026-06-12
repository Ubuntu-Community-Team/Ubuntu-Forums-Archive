---
title: "Raining when its raining"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by OneWingedAngel0164 on 2008-01-16
I reecently got ubuntu and fell in love with the rain effect then thought how awesome would it be to have it come on when it is raining. So far I have come up with this much for a shell script that works: 

dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/water/allscreens/toggle_rain org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4}'`

and this is what I have attempted to add to make it come on if its raining:

weather --id=KTLH | grep -q rain
if [[ "${?}" -eq "0"]] then
dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/water/allscreens/toggle_rain org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4}'`
fi

I don't know how to do if statements in shell yet. If I can get the shell script working, then  I can put it into crontab and have it check every 15 mins or so.

Anyone know how to fix my if and if this crazy idea will work?

Thanks,
Mike

---

### Post by bwhite82 on 2008-01-16
Sorry I'm no help, just wanted to add that this is a cool idea. Keep us posted.  :cool:

---

### Post by OneWingedAngel0164 on 2008-01-16
no one able to help? :(

---

### Post by Vanquish86 on 2008-01-16
Sorry I can't help either, but I love the idea.
Perhaps you'd get a better response in another sub-forum besides the absolute beginner one?

---

### Post by Sef on 2008-01-16
Please don't bump until 24 hours have passed; otherwise, you could get an infraction.

People in the forums are all volunteers, so sometimes it may take a while for your question to get answered.

You could also do a search and see if anyone else has solved your problem.

---

