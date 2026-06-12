---
title: "Macbook Load_Cycle_Count"
date: 2009-01-19
forum: Apple Hardware Users
---

### Post by TreeHugger52 on 2009-01-19
Hello all, I'm concerned about the Load_Cycle_Count on my macbook 4,1 running 8.10.

I know that there are MANY posts on many websites about this issue, and I'm aware of the Unofficial Ugly Fix ([http://ubuntuforums.org/showthread.php?t=805570](http://ubuntuforums.org/showthread.php?t=805570)). I don't want to reinvent the wheel and drag it through the mud again. My question is: have other macbook users found it necessary to change their hard drive's head parking parameters to extend the life of their hard drives? Have any macbook users had their HDD's fail 'early'?

Here's some output of sudo smartctl -a /dev/sda3. It looks pretty bleak (I think?), and this computer is less than a year old. Most of the output parameters are in old age or pre-fail. My Load_Cycle_Count is currently at 101168 and going up ~1/min, which isn't a huge rate of increase, but it's higher than I would like.


ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   046    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   030    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0003   100   100   025    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       4779
  5 Reallocated_Sector_Ct   0x0033   100   100   024    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   100   100   047    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   019    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   097   097   000    Old_age   Always       -       1791
 10 Spin_Retry_Count        0x0013   100   100   020    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       1742
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       201876570189
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       101168
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       35 (Lifetime Min/Max 14/48 )
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   253   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000f   100   100   060    Pre-fail  Always       -       0
203 Run_Out_Cancel          0x0002   100   100   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x003e   200   200   000    Old_age   Always       -       0

---

### Post by Rog-Mahal on 2009-01-19
Apparently the bug has been closed. Here's a[slashdot article]("http://http://it.slashdot.org/article.pl?sid=09/01/17/2127254") to that effect. I believe the update has already gone out.

---

