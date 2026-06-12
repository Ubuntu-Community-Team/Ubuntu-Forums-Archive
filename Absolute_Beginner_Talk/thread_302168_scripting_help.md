---
title: "scripting help"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by linkinPark on 2006-11-18
Hi

I am trying to create a script to automatically route ips through different ppp connections, here is what i have in my ip-up script:

```

case $PPP_LOCAL in
196.*)
        echo local: $PPP_LOCAL >/tmp/iplocal.txt;
        echo remote: $PPP_REMOTE >>/tmp/iplocal.txt;
        echo /32 routes go here > /tmp/routes.log;
        echo other routes go here > /tmp/routes1.log;
        echo no / routes go here > /tmp/routes2.log;
        for i in `cat /tmp/routefile.txt | dos2unix`; do
                if [[ $i =~ "/32" ]]; then echo route add -host $i gw $PPP_REMOTE >> /tmp/routes.log; route add -host $i gw $PPP_REMOTE >> /tmp/routes.log 2>&1;
                        else if [[ $i =~ "/" ]]; then echo route add -net $i gw $PPP_REMOTE >> /etc/ppp/routes1.log; route add -net $i gw $PPP_REMOTE >> /etc/ppp/routes1.log 2>&1;
                                else echo route add -net `echo -n $i | awk '{FS="." ; if ($1 >= 1 && $1 <= 126) {printf $0"/8"}else if ($1 >= 128 && $1 <= 191){printf $0"/16"}else if ($1 >= 192 && $1 <= 223){printf $0"/24"} }'` gw $PPP_REMOTE >> /etc/ppp/routes2.log; route add -net `echo -n $i | awk '{FS="." ; if ($1 >= 1 && $1 <= 126) {printf $0"/8"}else if ($1 >= 128 && $1 <= 191){printf $0"/16"}else if ($1 >= 192 && $1 <= 223){printf $0"/24"} }'` gw $PPP_REMOTE >> /etc/ppp/routes2.log 2>&1;
                        fi;
                fi;
        done;
;;
41.*)
        echo $PPP_LOCAL >/etc/ppp/ipint.txt
;;
165.*)
        echo $PPP_LOCAL >/etc/ppp/ipint.txt
;;
esac
```

Heres a sample from routefile.txt:

```
129.227.215.0/24
137.158.0.0
137.214.0.0
137.215.0.0
139.53.0.0
139.92.51.0/24
143.128.0.0
143.160.0.0
146.23.240.0/22
```

My problem is that is doesnt work unless i comment out the if statements, but if do that then it only creates the routes for the ips without the /
The first 5 echos, the last 2 and even the routes2.log in the awk statement work fine and even the for loop, but the if statements dont.

Someone please help me.

Thanks

---

