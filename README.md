# Linux-Process-API-fork-wait-exec-
Ex02-Linux Process API-fork(), wait(), exec()
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise


# AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

# PROGRAM:


## C Program to create new process using Linux API system calls fork() and getpid() , getppid() and to print process ID and parent Process ID using Linux API system calls

```
#include <stdio.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/wait.h>

int main()
{
    pid_t pid;

    pid = fork();

    if (pid < 0)
    {
        printf("Fork failed\n");
    }
    else if (pid == 0)
    {
        printf("Child Process\n");
        printf("Child PID: %d\n", getpid());
        printf("Parent PID: %d\n", getppid());
    }
    else
    {
        wait(NULL);
        printf("Parent Process\n");
        printf("Parent PID: %d\n", getpid());
        printf("Child PID: %d\n", pid);
    }

    return 0;
}

```


## OUTPUT


<img width="707" height="231" alt="image" src="https://github.com/user-attachments/assets/54a4f90c-f80a-4f32-a1d6-944ca7844e48" />





## C Program to execute Linux system commands using Linux API system calls exec() , exit() , wait() family




```
#include <stdio.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <stdlib.h>

int main()
{
    pid_t pid;

    pid = fork();

    if (pid == 0)
    {
        printf("Child process executing ls command\n");
        execlp("ls", "ls", "-l", NULL);
        perror("exec failed");
        exit(1);
    }
    else if (pid > 0)
    {
        wait(NULL);
        printf("Parent process completed\n");
    }
    else
    {
        printf("Fork failed\n");
    }

    return 0;
}
```





















## OUTPUT
<img width="675" height="235" alt="image" src="https://github.com/user-attachments/assets/bab42221-22e8-41e8-973b-2b3c19c70c88" />


















# RESULT:
The programs are executed successfully.
