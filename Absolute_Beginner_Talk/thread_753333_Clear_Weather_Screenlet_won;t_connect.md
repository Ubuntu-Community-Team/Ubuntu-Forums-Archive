---
title: "Clear Weather Screenlet won;t connect"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by PoopyTheJ on 2008-04-12
My Clear Weather Screenlet, and another weather screenlet won;t connect to weather.com. My internet connection is fine for browsing, UT2004, etc, but my screenlets won;t connect. What am I missing. The error I get is Could not reach Weather.com Check your internet connection and location and try again.

---

### Post by PoopyTheJ on 2008-04-12
I got it wrong Zip code format, in the US the City/State isn't necessary, ie I didn;t need UHOH4281, just 44281.

---

### Post by Hooya on 2008-05-06
Well, I'm having this problem trying to set it up and it doesn't matter what code I put in the zip field.  It always gives me that connection error problem.

Anyone else have any ideas?  I've tried all sorts of zip codes, even the default NY one gives me the error.

---

### Post by pubo68 on 2008-05-07
Hi, finally I solved the problem.
Reading "http://forum.compiz-fusion.org/showthread.php?t=8137&highlight=weather" and modifying the patch (basically i removed &prod=xoap at urlopen:.... lines), now I have working the Clear Weather screenlet properly on my PC.

Patch code:

--- ClearWeatherScreenlet.py	2008-04-03 14:57:21.000000000 -0400
+++ ClearWeatherScreenlet.py	2008-04-30 09:22:08.000000000 -0400
@@ -119,7 +119,7 @@
 		temp = self.parseWeatherData()
 		temp2 = self.parseWeatherDataHourly()
 		
-		if temp[0]["where"] == '':    ##did we get any data?  if not...
+		if len(temp) == 0 or temp[0]["where"]  == '':    ##did we get any data?  if not...
 			if self.show_error_message==1 and self.updated_recently == 1:
 				self.show_error()
 			self.updated_recently = 0
@@ -137,19 +137,23 @@
 			unit = 'm'
 		else:
 			unit = 's'
-		data = urlopen('http://xoap.weather.com/weather/local/'+self.ZIP+'?cc=*&dayf=10&prod=xoap&par=1003666583&key=4128909340a9b2fc&unit='+unit).read()
+
 		forecast = []
+		try:
+			data = urlopen('http://xoap.weather.com/weather/local/'+self.ZIP+'?cc=*&dayf=10&par=1003666583&key=4128909340a9b2fc&unit='+unit).read()
 
-		dcstart = data.find('<loc ')
-		dcstop = data.find('</cc>')     ###### current conditions
-		data_current = data[dcstart:dcstop]
-		forecast.append(self.tokenizeCurrent(data_current))
-
-		for x in range(10):
-			dcstart = data.find('<day d=\"'+str(x))
-			dcstop = data.find('</day>',dcstart)   #####10-day forecast
-			day = data[dcstart:dcstop]
-			forecast.append(self.tokenizeForecast(day))
+			dcstart = data.find('<loc ')
+			dcstop = data.find('</cc>')     ###### current conditions
+			data_current = data[dcstart:dcstop]
+			forecast.append(self.tokenizeCurrent(data_current))
+
+			for x in range(10):
+				dcstart = data.find('<day d=\"'+str(x))
+				dcstop = data.find('</day>',dcstart)   #####10-day forecast
+				day = data[dcstart:dcstop]
+				forecast.append(self.tokenizeForecast(day))
+		except IOError, e:
+			print "Error retreiving Weather Data", e
 
 		return forecast
 
@@ -159,14 +163,17 @@
 			unit = 'm'
 		else:
 			unit = 's'
-		data = urlopen('http://xoap.weather.com/weather/local/'+self.ZIP+'?cc=*&dayf=10&prod=xoap&par=1003666583&key=4128909340a9b2fc&unit='+unit+'&hbhf=12').read()
-		hforecast = []
 
-		for x in range(8):
-			dcstart = data.find('<hour h=\"'+str(x))
-			dcstop = data.find('</hour>',dcstart)   ####hourly forecast
-			hour = data[dcstart:dcstop]
-			hforecast.append(self.tokenizeForecastHourly(hour))
+		hforecast = []
+		try:
+			data = urlopen('http://xoap.weather.com/weather/local/'+self.ZIP+'?cc=*&dayf=10&par=1003666583&key=4128909340a9b2fc&unit='+unit+'&hbhf=12').read()
+			for x in range(8):
+				dcstart = data.find('<hour h=\"'+str(x))
+				dcstop = data.find('</hour>',dcstart)   ####hourly forecast
+				hour = data[dcstart:dcstop]
+				hforecast.append(self.tokenizeForecastHourly(hour))
+		except IOError, e:
+			print "Error retrieving weather data", e
 
 		return hforecast

---

### Post by Kevbert on 2008-05-07
See this thread: [http://ubuntuforums.org/showthread.php?t=784053&highlight=weather]("http://ubuntuforums.org/showthread.php?t=784053&highlight=weather")

Weather.com have changed some of their links.

---

### Post by dexgen on 2008-05-08
Thanks a lot pubo68! This actually works! Just removed the &prod=xoap and it worked like a charm :)

---

### Post by elamericano on 2008-05-08
Pubo, what's with the huge patch? Just open /usr/share/screenlets/ClearWeather/ClearWeatherScreenlet.py with you favorite editor. Remove the two occurrences of &prod=xoap, and save it. Then Re-start all screenlets. (Look, 71 degrees tomorrow.)

That'll do until an update comes down.

---

### Post by lsutiger on 2008-05-10
I tried the patch but got errors. I tried editing the python script, but it did not work. 
restarted all screnlets, same error.

I am attaching my clearweather python script for you to review.
Thanx in advance!

---

### Post by Martin Aulbach on 2008-05-11
> **dexgen said:**
> Thanks a lot pubo68! This actually works! Just removed the &prod=xoap and it worked like a charm :)

That worked perfectly for me, thanks! It's really as easy as removing the two occurrences of this string from the py file.

---

### Post by elamericano on 2008-05-12
lsutiger: You have version 0.4. Version 0.3 is in the repos, and that is the one that can be fixed by this method.

---

### Post by xboxSlayer on 2008-05-15
Remove the two occurrences of &prod=xoap, and save it. Then Re-start all screenlets.

Worked for me for version 0.4

---

### Post by jonlong on 2008-05-17
I am new to linux and ubuntu and am having the same problem.  How do I access the script to make the changes suggested earlier in this thread?

Thanks!

---

