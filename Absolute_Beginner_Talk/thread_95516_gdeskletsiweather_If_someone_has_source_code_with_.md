---
title: "gdesklets:iweather: If someone has source code with bigger fonts, i am interested !!"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-11-26
(too small fonts for the day and temperature)
how to change it ?
  
my source code:
```
<?xml version="1.0" encoding="UTF-8"?>
<display window-flags="sticky, below">
<sensor id="w" module="iWeather"/>
<group id="canvas" >
  <group id="today">
    <image id="ccIcon" x="0" y="0" watch="uri=w:ccIcon, color=f:color1, font=f:font1"/>
    <label id="ccTemp" relative-to="ccIcon, x" x="0" y="0" watch="value=w:ccTemp" color="white" font="Sans bold 25"/>
    <label id="location" relative-to="ccTemp, y" watch="value=w:location" color="#f0f0f0" font="Sans bold 20"/>
    <label id="ccFlik" relative-to="location, y" watch="value=w:ccFlik" color="#f0f0f0" font="Sans bold 20"/>
    <label id="ccWind" relative-to="ccFlik, y" watch="value=w:ccWind" color="#f0f0f0" font="Sans bold 20"/>
    <label id="ccHmid" relative-to="ccWind, y" watch="value=w:ccHmid" color="#f0f0f0" font="Sans bold 20"/>
  </group>
  <group id="forecast" relative-to="today, x" x="20" y="0" watch="color=f:color0, font=f:font0">
    <array layout="horizontal" watch="length=w:forecastDays">
      <group id="forecastDay" x="20">
        <label id="forecastDay" color="white" watch="value=w:forecastDay" />
        <group id="dayNight" relative-to="forecastDay, y">
          <group id="day">
            <image id="forecastDayIcon" anchor="n" watch="uri=w:forecastDayIcon" />
            <label id="forecastTempHi" anchor="n" relative-to="forecastDayIcon, y" color="white" watch="value=w:forecastTempHi" />
            <label id="forecastSunrise" anchor="n" relative-to="forecastTempHi, y" color="white" watch="value=w:forecastSunrise" />
          </group>
          <group id="night" relative-to="day, x" x="5">
            <image id="forecastNightIcon" anchor="n" watch="uri=w:forecastNightIcon" />
            <label id="forecastTempLow" anchor="n" relative-to="forecastNightIcon, y" color="white" watch="value=w:forecastTempLow" />
            <label id="forecastSunset" anchor="n" relative-to="forecastTempLow, y" color="white" watch="value=w:forecastSunset" />
          </group>
        </group>
      </group>
    </array>
  </group>
</group>
</display>

```

Thank you very much !
**[SIZE="4"]also how to change the GREY color of background of iweather to BLUE ??[/SIZE]**

---

### Post by Xian on 2005-11-26
I don't have a direct answer, but I do know that the [Good Weather](http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=204) desklet will let you configure the font sizes from a GUI menu.

---

