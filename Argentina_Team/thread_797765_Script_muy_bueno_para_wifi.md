---
title: "Script muy bueno para wifi"
date: 2008-05-17
forum: Argentina Team
---

### Post by sergiom99 on 2008-05-17
Encontre este script para que tu compu "te cante" la senial si estas orientando antenas.
A mi me sirvio, pero no importa como la movia nunca pude pasar de -70 en el lugar de menor calidad.

```
#! /bin/bash
# Use "festival" to say out loud how much signal strength we have

# The ip address of the WRT
ip_addr="192.168.1.1"

# The username and password for the WRT
user="root"
pass="admin"

# Tempory file used to hold the data from the WRT
tmp_file=/tmp/wrt.status

echo
echo "The signal level is:-"
echo
echo "The signal level is" | festival --tts

while true ; do
       wget --http-user=$user --http-password=$pass http://$ip_addr/Status_Wireless.live.asp -O $tmp_file -o /dev/null
 
        signal=`awk  -F "'" '/active_wireless/ { print  $8 }' $tmp_file`
 
        echo $signal | awk '{printf"Signal  :  "$1"\t";for(;j<$1;j++)printf"=";printf"\n"}'

        if [[ -n $signal ]] ; then 
                echo $signal | festival --tts
        else
                echo "Not associated" | festival --tts
        fi
done
```
[Les dejo el link original por las dudas.
[http://www.dd-wrt.com/wiki/index.php/Useful_Scripts#Speak_Your_Signal_Strength]](http://www.dd-wrt.com/wiki/index.php/Useful_Scripts#Speak_Your_Signal_Strength])

Para que festival me funcione tuve que crear este archivo:
```
printf ";use ALSA\n(Parameter.set 'Audio_Method 'Audio_Command)\n(Parameter.set 'Audio_Command \"aplay -q -c 1 -t raw -f s16 -r \$SR \$FILE\")\n" > ~/.festivalrc
```

Salutes y espero le sirva a alguno.

PS: Aclaro que el script solo funciona si tenes un router con el firmware de dd-wrt.com.

---

### Post by elgatovolador on 2008-05-17
Intenté correrlo, pero no se a q se refiere con WRT... ni que archivo es ese Status_Wireless.live.asp

---

### Post by sergiom99 on 2008-05-17
> **elgatovolador said:**
> Intenté correrlo, pero no se a q se refiere con WRT... ni que archivo es ese Status_Wireless.live.asp

solo funciona si tenes un router con el firmware de dd-wrt.com.
En mi caso: DD-WRT v24 RC-5 (11/22/07) micro

---

