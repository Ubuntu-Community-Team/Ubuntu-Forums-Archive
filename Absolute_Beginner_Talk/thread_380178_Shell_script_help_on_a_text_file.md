---
title: "Shell script help on a text file"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by Bagboy23 on 2007-03-09
Hi guys,

I'm trying to extract the values from this Xml feed:

[http://feeds.bbc.co.uk/weather/feeds/rss/5day/world/4581.xml](http://feeds.bbc.co.uk/weather/feeds/rss/5day/world/4581.xml)

```
<?xml version="1.0" encoding="UTF-8"?>
<?xml-stylesheet type="text/xsl" href="http://feeds.bbc.co.uk/weather/feeds/rss/5day/weather.xsl"?>

<rss version="2.0"  xmlns:geo="http://www.w3.org/2003/01/geo/wgs84_pos#" >

<channel>
<title>BBC - Weather Centre - Forecast for London City, United Kingdom</title>
<link>http://feeds.bbc.co.uk/weather/feeds/rss/5day/world/4581.xml</link>
<description>by the BBC Weather Centre in association with the Met Office</description>
<language>en</language>
<copyright>Copyright: (C) British Broadcasting Corporation</copyright>
<pubDate>Fri, 09 Mar 2007 07:52:01 +0000</pubDate>

<lastBuildDate>Fri, 09 Mar 2007 07:52:01 +0000</lastBuildDate>
<managingEditor>weather@bbc.co.uk</managingEditor>
<webMaster>weather@bbc.co.uk</webMaster>

<item>
<title>The forecast for London City, United Kingdom on Friday: sunny.  Max Temp: 13&#xB0;C (55&#xB0;F), Min Temp: 5&#xB0;C (41&#xB0;F), Wind Direction: NW, Wind Speed: 12mph</title>
<link>http://www.bbc.co.uk/weather/5day.shtml?world=4581</link>
<description>The forecast for London City, United Kingdom on Friday: sunny.  Max Temp: 13&#xB0;C (55&#xB0;F), Min Temp: 5&#xB0;C (41&#xB0;F), Wind Direction: NW, Wind Speed: 12mph, Visibility: moderate, Pressure: 1027mb, Humidity: 38%, UV risk: low, Pollution: low, Sunrise: 06:30GMT, Sunset: 17:51GMT</description>

<guid isPermaLink="false">tag:feeds.bbc.co.uk,2007-03-09:/weather/5day/world/4581</guid>
<pubDate>Fri, 09 Mar 2007 07:52:01 +0000</pubDate>
<geo:lat>51.52</geo:lat>
<geo:long>-0.1</geo:long>
</item>

</channel>
</rss>
```

The output of the XML file is:

> BBC - Weather Centre - Forecast for London City, United Kingdom

          
by the BBC Weather Centre in association with the Met Office

      
The forecast for London City, United Kingdom on Friday: **sunny**.  Max Temp: 13°C (55°F), Min Temp: 5°C (41°F), **Wind Direction: NW**, **Wind Speed: 12mph**

The forecast for London City, United Kingdom on Friday: sunny.  Max Temp: 13°C (55°F), Min Temp: 5°C (41°F), Wind Direction: NW, Wind Speed: 12mph, Visibility: moderate, Pressure: 1027mb, Humidity: 38%, UV risk: low, Pollution: low, Sunrise: 06:30GMT, Sunset: 17:51GMT

Now what I want to do is, download that file every 3 hours and format the display (from the items in bold) into a normal txt document as:

[b]sunny
Wind Direction: NW
Wind Speed: 12mph[/b]

Now, here is my plan: 

Wget [http://feeds.bbc.co.uk/weather/feeds/rss/5day/world/4581.xml](http://feeds.bbc.co.uk/weather/feeds/rss/5day/world/4581.xml)

pause (3 hours)

Extract and Format the text

Save output to weather.txt


Now, I just don't know where to begin with the formating. I've spent all morning trying to Cat and sed it together, but it's just so complicated. I'm completely lost right now.

Any help would be appreciated. :guitar:

---

### Post by LotsOfPhil on 2007-03-09
```

wget http://feeds.bbc.co.uk/weather/feeds/rss/5day/world/4581.xml -q
                                                                                
sed -n /\<title\>The/p 4581.xml > text
                                                                                
weather=`awk -F: '{print $2}' text`
winddir=`awk -F: '{print $5}' text`
windspeed=`awk -F: '{print $6}' text`
                                                                                
weather=${weather%.*}
winddir=${winddir%,*}
windspeed=${windspeed%<*}
                                                                                
echo "Forecast: $weather" > weather.txt
echo "Wind Direction: $winddir" >> weather.txt
echo "Wind Speed: $windspeed" >> weather.txt
                                                                                
rm 4581.xml text

```

---

### Post by LotsOfPhil on 2007-03-09
Now, this is a very dumb script. It won't be able to handle if there are any changes in the XML file at all.

---

### Post by Bagboy23 on 2007-03-09
Thanks for the script LotsofPhil. I'm looking forward to trying this out at home.

I'm going on the assumption that this Xml file will not change as I've kept an eye on it for quite some time (4 months).

Thanks again. I'll let you know how it went. :)



Edit. Ok, crap I just did a comparison of a before and after of the Xml script (4 months ago) and you're right it changed.

That was such a cool script it did the stuff but it's not handling the change.

---

### Post by LotsOfPhil on 2007-03-09
What is changing? It is entirely possible to make it smarter.

---

### Post by Bagboy23 on 2007-03-10
Thanks Lotofphil, my mistake I accidentallu bodged upone of the files so did not work.

Thanks again, it is perfect.

---

### Post by Bagboy23 on 2007-03-13
Lotsofphil, can I have the script modified slightly to include:

windspeed with just the number, without the mph. So the example below would just give 12.

Also can I have added to the script; Visibility and sunrise and sunset without the GMT? I just need the info without the field name, for instance:

moderate
06:30
17:51

would come from:

Visibility
sunrise
sunset

I would really appreciate the help as I thought I could work it out, but I'm just totally stuck and have been so for two days now.

Many thanks in advance.

---

### Post by LotsOfPhil on 2007-03-13
```

#!/bin/bash
wget http://feeds.bbc.co.uk/weather/feeds/rss/5day/world/4581.xml -q
 
sed -n /\<description\>The/p 4581.xml > text
 
weather=`awk -F: '{print $2}' text`
winddir=`awk -F: '{print $5}' text`
windspeed=`awk -F: '{print $6}' text`
visibility=`awk -F: '{print $7}' text`
sunrise=`awk -F: '{print $12 ":" $13}' text`
sunset=`awk -F: '{print $14 ":" $15}' text`
 
weather=${weather%.*}
winddir=${winddir%,*}
windspeed=${windspeed%mph*}
visibility=${visibility%,*}
sunrise=${sunrise%GMT*}
sunset=${sunset%GMT*}
 
echo $weather > weather.txt
echo $winddir >> weather.txt
echo $windspeed >> weather.txt
echo $visibility >> weather.txt
echo $sunrise >> weather.txt
echo $sunset >> weather.txt
 
rm 4581.xml text

```

And output:
```

sunny intervals
W
3
moderate
06:22
17:58

```

---

