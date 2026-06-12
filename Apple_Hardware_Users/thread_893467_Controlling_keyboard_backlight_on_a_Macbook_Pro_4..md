---
title: "Controlling keyboard backlight on a Macbook Pro 4.1 (Penryn)"
date: 2008-08-18
forum: Apple Hardware Users
---

### Post by oricordeau on 2008-08-18
Hi there,

I have a last generation macbook pro (4.1 Penryn) and I finally managed to get the keyboard backlight working with Ubuntu. I'm talking about being able to control the backlight's intensity from the command line, not having the backlight adjusting itself automatically. Here is the trick.
[LIST]
[*]Get the "tools" directory from the mactel-linux SVN repository: "svn checkout http://mactel-linux.svn.sourceforge.net/svnroot/mactel-linux/trunk/tools mactel-linux-tools"
[*]Change the current directory to the newly created directory "cd mactel-linux-tools"
[*]Initialy, the brightness is set to 0 (intensity values are between 0 and 255). Execute this command to switch the backlight to the maximum level: "sudo ./keyboard_brigthness 255"
[*]Then, you can use the following command to switch the light on and off: "sudo ./keyboard_brigthness toggle"
[/LIST]
I added an application launcher that switches the light on and off using the "keyboard_brigthness" script (with gksudo).

Remark: I'm still unable to get the backlight automatically adjusting itself according to the ambient light with pommed. It switches the light on for a few seconds and then it switches off (though there is still no ambient light).

Cheers,
Olivier

---

### Post by hajk on 2008-08-18
Interesting! Does this use the applesmc module? If so, does it still fill up the logs (/var/log/syslog, /var/log/messages) with debugging/error messages?

---

### Post by oricordeau on 2008-08-18
> **hajk said:**
> Interesting! Does this use the applesmc module? If so, does it still fill up the logs (/var/log/syslog, /var/log/messages) with debugging/error messages?

Yes, it uses the applesmc module. And yes, my logs are still filled with "applesmc: wait status failed: c != 8".

Olivier

---

### Post by rmartins on 2008-08-19
Hi there,

I am also unable to have auto keyboard backlight on my macbook pro 4.1. I managed to find out,
that the applesmc module has some problem:
"cat /sys/devices/platform/applesmc.768/light" => " Input/output error"
This is causing problems to pommed (as it can't access the ambient sensor).

I tested Ubuntu Hardy and Fedora 9, and they have the same problem.

I used a rude hack to test a bit (used code from smc_tools). The
values I get are a bit erratic. I get (-1,some_value_bigger_than_0) or
(some_value_bigger_than_0,-1), so I reset the negative value...

(File: pommed-1.21/pommed/mactel/ambient.c)

static int light_first_time = 0;
void inline ssleep(const int usec) {
  gettimeofday(&lasttv, NULL);
  while (1) {
     gettimeofday(&newtv, NULL);
     if (((newtv.tv_usec - lasttv.tv_usec) + ((newtv.tv_sec -
lasttv.tv_sec)*1000000)) > usec) {
        break;
     }
  }
}

unsigned char get_status() {
       return inb(0x304);
}


int waitfree(char num) {
       char c, pc = -1;
       int retry = 100;
       while (((c = get_status())&0x0F) != num && retry) {
               ssleep(10);
               retry--;
               if (pc != c) {
                       //printf("%x-%d:", c, retry);
                       pc = c;
               }
       }
       if (retry == 0) {
         //printf("Waitfree failed %x != %x.\n", c, num);
               return 0;
       }
       /*else
               printf("Waitfree ok %x.\n", c);*/

       return 1;
}
static int light_first_time = 0;

int readkey(char* key, char len, unsigned char* buffer) {
       int i; unsigned char c;
       if(light_first_time == 0){
         light_first_time = 1;
         if (ioperm(0x300, 0x304, 1) < 0) {
           perror("ioperm failed (you should be root).");
           exit(-1);
       }
       }
       outb(0x10, 0x304);
       if (!waitfree(0x0c)) return 0;

       for (i = 0; i < 4; i++) {
               outb(key[i], 0x300);
               if (!waitfree(0x04)) return 0;
       }
       if (debug) printf("<%s", key);

       outb(len, 0x300);
       if (debug) printf(">%x", len);

       for (i = 0; i < len; i++) {
               if (!waitfree(0x05)) return 0;
               c = inb(0x300);
               buffer[i] = c;
               if (debug) printf("<%x", c);
       }
       if (debug) printf("\n");
       return 1;
}

int read_light_sensor(int left) {
       unsigned char buffer[6];
       if (readkey(left ? LIGHT_SENSOR_LEFT_KEY : LIGHT_SENSOR_RIGHT_KEY, 6, buffer))
               return buffer[2];
       else
               return -1;
}

void ambient_get_i(int *r, int *l)
{
 int i;
 *r = -1;
 *l = -1;
 for(i=0; i < LIGHT_MAX_TRIES; i++){
   if(*l == -1 || *r==-1){
     if(*l == -1){
       *l = read_light_sensor(1);
     }
     if(*r == -1){
       *r = read_light_sensor(0);
     }
   }else{
     break;
   }
 }
 if(*l == -1 && *r>=0){
   *l = *r;
 }
 if(*r == -1 && *l>=0){
   *r = *l;
 }

 if(*r < *l){
   *r = *l;
 }else{
   *l = *r;
 }
 printf("R=%d L=%d\n",*r,*l);

}


void
ambient_get(int *r, int *l)
{
 int fd;
 int ret;
 char buf[16];
 char *p;

 ambient_get_i(r,l);
 if(*l == -1 && *r == -1){
   *r = -1;
   *l = -1;
   ambient_info.right = 0;
   ambient_info.left = 0;
 }else{
   ambient_info.right = *r;
   ambient_info.left = *l;
 }

 return;
//end of hack

 fd = open(smcpath, O_RDONLY);
 if (fd < 0)
   {
     *r = -1;
     *l = -1;

     ambient_info.right = 0;
     ambient_info.left = 0;

     return;
   }

 ret = read(fd, buf, 16);

 close(fd);

 if ((ret <= 0) || (ret > 15))
   {
     *r = -1;
     *l = -1;

     ambient_info.right = 0;
     ambient_info.left = 0;

     return;
   }

 buf[strlen(buf)] = '\0';

 p = strchr(buf, ',');
 *p++ = '\0';
 *r = atoi(p);

 p = buf + 1;
 *l = atoi(p);

 logdebug("Ambient light: right %d, left %d\n", *r, *l);

 ambient_info.right = *r;
 ambient_info.left = *l;
}

Hope it helps,
Rolando

---

