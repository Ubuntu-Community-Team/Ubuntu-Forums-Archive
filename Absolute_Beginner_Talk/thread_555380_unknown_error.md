---
title: "unknown error"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by nishanthaMe on 2007-09-20
I compiled folloiwng C programe and it gives some errors.Can anyone know the reasons.I copied the programe from a PDF and compiled.
programe :

#include  <stdlib.h>
#include  <stdio.h>
#include  <netinet/in.h>
#include  <netdb.h>
#include  <sys/socket.h>
#include  <unistd.h>
#include  <string.h>
/* Print the contents of the home page for the server’s socket.
   Return an indication of success. */
void get_home_page (int socket_fd)
{
  char buffer[10000];
  ssize_t number_characters_read;
  /* Send the HTTP GET command for the home page. */
  sprintf (buffer, “GET /”);
  write (socket_fd, buffer, strlen (buffer));
  /* Read from the socket. The call to read may not
  return all the data at one time, so keep
  trying until we run out. */
  while (1) {
    number_characters_read = read (socket_fd, buffer, 10000);
    if (number_characters_read == 0)
       return;
    /* Write the data to standard output. */
    fwrite (buffer, sizeof (char), number_characters_read, stdout);
  }
}
int main (int argc, char* const argv[])
{
  int socket_fd;
  struct sockaddr_in name;
  struct hostent* hostinfo;
  /* Create the socket. */
  socket_fd = socket (PF_INET, SOCK_STREAM, 0);
  /* Store the server’s name in the socket address. */
  name.sin_family = AF_INET;
  /* Convert from strings to numbers. */
  hostinfo = gethostbyname (argv[1]);
  if (hostinfo == NULL)
    return 1;
  else
    name.sin_addr = *((struct in_addr *) hostinfo->h_addr);
  /* Web servers use port 80. */
  name.sin_port = htons (80);
  /* Connect to the Web server */
  if (connect (socket_fd, &name, sizeof (struct sockaddr_in)) == -1) {
    perror (“connect”);
    return 1;
  }
  /* Retrieve the server’s home page. */
  get_home_page (socket_fd);
  return 0;
}
...............................................................
error:

test.c: In function ‘get_home_page’:
test.c:15: error: stray ‘\226’ in program
test.c:15: error: stray ‘\128’ in program
test.c:15: error: stray ‘\156’ in program
test.c:15: error: ‘GET’ undeclared (first use in this function)
test.c:15: error: (Each undeclared identifier is reported only once
test.c:15: error: for each function it appears in.)
test.c:15: error: stray ‘\226’ in program
test.c:15: error: stray ‘\128’ in program
test.c:15: error: stray ‘\157’ in program
test.c:15: error: syntax error before ‘)’ token
test.c: In function ‘main’:
test.c:46: warning: passing argument 2 of ‘connect’ from incompatible pointer type
test.c:47: error: stray ‘\226’ in program
test.c:47: error: stray ‘\128’ in program
test.c:47: error: stray ‘\156’ in program
test.c:47: error: stray ‘\226’ in program
test.c:47: error: stray ‘\128’ in program
test.c:47: error: stray ‘\157’ in program
test.c:47: warning: passing argument 1 of ‘perror’ from incompatible pointer type

---

### Post by rsambuca on 2007-09-20
Maybe a mod can move this to "Programming Talk".  I think this may scare off some of the Absolute Beginners!

---

### Post by Wim Sturkenboom on 2007-09-20
Your file is 'corrupted'. There are funny characters in there like the double quotes in line 15. This line should read
```
sprintf (buffer, "GET /");
```instead of
```
sprintf (buffer, “GET /”);
```

---

### Post by nishanthaMe on 2007-09-20
It is ok.I also agree with you.

---

