---
title: "can u write script for  martian_modem /dev/modem"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by sherirao on 2007-05-08
i connect to internet through 56k modem and i have to execute following commands . . . . . 
1st : sudo [COLOR="DimGray"]martian_modem /dev/modem[/COLOR]
then in separate terminal 
2nd: [COLOR="DimGray"]sudo wvdial[/COLOR] 

Can anyone automate this task for me , something 1-click thingy :)

---

### Post by Carlos Santiago on 2007-05-08
Try making like this. Create a file with

```
gsudo martian_modem /dev/modem && wvdial 
```

Save it as 'connect' in your desktop (~/Desktop/connect)

Then give it execution permitions:
```
chmod +x ~/Desktop/connect
```

On your Desktop you should now find the 'connect' application. Double click it!

---

### Post by sherirao on 2007-05-16
i followed the procedure but it goes upto opening port (running martian) but fail to run wvdial , even when it is executed , wvdial doesn't even work in separate terminal , i have to restart martian again to make wvdial work , 
double trouble! pls help ...

---

### Post by a10 on 2008-02-23
Well this topic is a little old but here´s a little script that I wrote that works:
```
#
#Shane´s script to setup the modem
#
#

#if the modem is setup then don´t bother
if ls /dev | grep modem > /dev/null
then
	echo ¨Already Setup...¨
else	
	#if martian driver is there don´t bother
	if lsmod | grep martian_dev > /dev/null
	then
		echo ¨Driver´s Setup...¨
	else
		sudo modprobe martian_dev
	fi

	echo ¨Launching martian_Modem...¨
	(sudo xterm -e martian_modem /dev/modem) &
	echo ¨Dialing¨
	(sudo xterm -e wvdial) &
fi

echo ¨Script Completed¨
```

On an unrelated note, Does anyone know how to close an instance of martian_modem?
I don´t know how to kill it.

---

