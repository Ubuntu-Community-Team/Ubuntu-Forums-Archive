---
title: "make deosnt work?"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by haxer on 2006-11-25
Hello i recently downloaded something to my Desktop 

So i first untered it then i 

cd /home/open/Desktop/openmortal-0.7

then i used ./configure 

then i used make 

bash: make: command not found 

wtf ... why cant i use the command make?

---

### Post by junglepeanut on 2006-11-25
Install build-essential to compile

---

### Post by haxer on 2006-11-25
In synaptic? build-essential ?

---

### Post by taurus on 2006-11-25
```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by junglepeanut on 2006-11-25
yes, or

sudo aptitude install build-essential

they are essential!

---

### Post by haxer on 2006-11-25
Thanks :)

---

### Post by highneko on 2006-11-25
[color="#ff0000"]a[/color][color="#ff0101"]a[/color][color="#ff0202"]a[/color][color="#ff0303"]a[/color][color="#ff0404"]a[/color][color="#ff0505"]a[/color][color="#ff0606"]a[/color][color="#ff0707"]a[/color][color="#ff0808"]a[/color][color="#ff0909"]a[/color][color="#ff0a0a"]a[/color][color="#ff0b0b"]a[/color][color="#ff0c0c"]a[/color][color="#ff0d0d"]a[/color][color="#ff0e0e"]a[/color][color="#ff0f0f"]a[/color][color="#ff1010"]a[/color][color="#ff1111"]a[/color][color="#ff1212"]a[/color][color="#ff1313"]a[/color][color="#ff1414"]a[/color][color="#ff1515"]a[/color][color="#ff1616"]a[/color][color="#ff1717"]a[/color][color="#ff1818"]a[/color][color="#ff1919"]a[/color][color="#ff1a1a"]a[/color][color="#ff1b1b"]a[/color][color="#ff1c1c"]a[/color][color="#ff1d1d"]a[/color][color="#ff1e1e"]a[/color][color="#ff1f1f"]a[/color][color="#ff2020"]a[/color][color="#ff2121"]a[/color][color="#ff2222"]a[/color][color="#ff2323"]a[/color][color="#ff2424"]a[/color][color="#ff2525"]a[/color][color="#ff2626"]a[/color][color="#ff2727"]a[/color][color="#ff2828"]a[/color][color="#ff2929"]a[/color][color="#ff2a2a"]a[/color][color="#ff2b2b"]a[/color][color="#ff2c2c"]a[/color][color="#ff2d2d"]a[/color][color="#ff2e2e"]a[/color][color="#ff2f2f"]a[/color][color="#ff3030"]a[/color][color="#ff3131"]a[/color][color="#ff3232"]a[/color][color="#ff3333"]a[/color][color="#ff3434"]a[/color][color="#ff3535"]a[/color][color="#ff3636"]a[/color][color="#ff3737"]a[/color][color="#ff3838"]a[/color][color="#ff3939"]a[/color][color="#ff3a3a"]a[/color][color="#ff3b3b"]a[/color][color="#ff3c3c"]a[/color][color="#ff3d3d"]a[/color][color="#ff3e3e"]a[/color][color="#ff3f3f"]a[/color][color="#ff4040"]a[/color][color="#ff4141"]a[/color][color="#ff4242"]a[/color][color="#ff4343"]a[/color][color="#ff4444"]a[/color][color="#ff4545"]a[/color][color="#ff4646"]a[/color][color="#ff4747"]a[/color][color="#ff4848"]a[/color][color="#ff4949"]a[/color][color="#ff4a4a"]a[/color][color="#ff4b4b"]a[/color][color="#ff4c4c"]a[/color][color="#ff4d4d"]a[/color][color="#ff4e4e"]a[/color][color="#ff4f4f"]a[/color][color="#ff5050"]a[/color][color="#ff5151"]a[/color][color="#ff5252"]a[/color][color="#ff5353"]a[/color][color="#ff5454"]a[/color][color="#ff5555"]a[/color][color="#ff5656"]a[/color][color="#ff5757"]a[/color][color="#ff5858"]a[/color][color="#ff5959"]a[/color][color="#ff5a5a"]a[/color][color="#ff5b5b"]a[/color][color="#ff5c5c"]a[/color][color="#ff5d5d"]a[/color][color="#ff5e5e"]a[/color][color="#ff5f5f"]a[/color][color="#ff6060"]a[/color][color="#ff6161"]a[/color][color="#ff6262"]a[/color][color="#ff6363"]a[/color][color="#ff6464"]a[/color][color="#ff6565"]a[/color][color="#ff6666"]a[/color][color="#ff6767"]a[/color][color="#ff6868"]a[/color][color="#ff6969"]a[/color][color="#ff6a6a"]a[/color][color="#ff6b6b"]a[/color][color="#ff6c6c"]a[/color][color="#ff6d6d"]a[/color][color="#ff6e6e"]a[/color][color="#ff6f6f"]a[/color][color="#ff7070"]a[/color][color="#ff7171"]a[/color][color="#ff7272"]a[/color][color="#ff7373"]a[/color][color="#ff7474"]a[/color][color="#ff7575"]a[/color][color="#ff7676"]a[/color][color="#ff7777"]a[/color][color="#ff7878"]a[/color][color="#ff7979"]a[/color][color="#ff7a7a"]a[/color][color="#ff7b7b"]a[/color][color="#ff7c7c"]a[/color][color="#ff7d7d"]a[/color][color="#ff7e7e"]a[/color][color="#ff7f7f"]a[/color][color="#ff8080"]a[/color][color="#ff8181"]a[/color][color="#ff8282"]a[/color][color="#ff8383"]a[/color][color="#ff8484"]a[/color][color="#ff8585"]a[/color][color="#ff8686"]a[/color][color="#ff8787"]a[/color][color="#ff8888"]a[/color][color="#ff8989"]a[/color][color="#ff8a8a"]a[/color][color="#ff8b8b"]a[/color][color="#ff8c8c"]a[/color][color="#ff8d8d"]a[/color][color="#ff8e8e"]a[/color][color="#ff8f8f"]a[/color][color="#ff9090"]a[/color][color="#ff9191"]a[/color][color="#ff9292"]a[/color][color="#ff9393"]a[/color][color="#ff9494"]a[/color][color="#ff9595"]a[/color][color="#ff9696"]a[/color][color="#ff9797"]a[/color][color="#ff9898"]a[/color][color="#ff9999"]a[/color][color="#ff9a9a"]a[/color][color="#ff9b9b"]a[/color][color="#ff9c9c"]a[/color][color="#ff9d9d"]a[/color][color="#ff9e9e"]a[/color][color="#ff9f9f"]a[/color][color="#ffa0a0"]a[/color][color="#ffa1a1"]a[/color][color="#ffa2a2"]a[/color][color="#ffa3a3"]a[/color][color="#ffa4a4"]a[/color][color="#ffa5a5"]a[/color][color="#ffa6a6"]a[/color][color="#ffa7a7"]a[/color][color="#ffa8a8"]a[/color][color="#ffa9a9"]a[/color][color="#ffaaaa"]a[/color][color="#ffabab"]a[/color][color="#ffacac"]a[/color][color="#ffadad"]a[/color][color="#ffaeae"]a[/color][color="#ffafaf"]a[/color][color="#ffb0b0"]a[/color][color="#ffb1b1"]a[/color][color="#ffb2b2"]a[/color][color="#ffb3b3"]a[/color][color="#ffb4b4"]a[/color][color="#ffb5b5"]a[/color][color="#ffb6b6"]a[/color][color="#ffb7b7"]a[/color][color="#ffb8b8"]a[/color][color="#ffb9b9"]a[/color][color="#ffbaba"]a[/color][color="#ffbbbb"]a[/color][color="#ffbcbc"]a[/color][color="#ffbdbd"]a[/color][color="#ffbebe"]a[/color][color="#ffbfbf"]a[/color][color="#ffc0c0"]a[/color][color="#ffc1c1"]a[/color][color="#ffc2c2"]a[/color][color="#ffc3c3"]a[/color][color="#ffc4c4"]a[/color][color="#ffc5c5"]a[/color][color="#ffc6c6"]a[/color][color="#ffc7c7"]a[/color][color="#ffc8c8"]a[/color][color="#ffc9c9"]a[/color]

---

