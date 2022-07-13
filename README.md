# templates
Template codes

`date +%Y%m%d%-H%M%S`

stdout and stderr 1 and 2 to separate files
```
exec 1>>${LOG_FILE}
exec 2>>${LOG_FILE}
```

Other options:
```
exec 3>&1 4>&2
trap 'exec 2>&4 1>&3' 0 1 2 3
exec 1>log.out 2>&1
```
[Source](https://serverfault.com/questions/103501/how-can-i-fully-log-all-bash-scripts-actions)

Checking if file and directory exists
```
check_file_exists() {
    if [ ! -f "$1" ]; then
        echo "[trim.sh] error: file '$1' does not exist." >&2
        exit
    fi
}

check_dir_exists() {
    if [ ! -d "$1" ]; then
        echo "[trim.sh] error: directory '$1' does not exist, creating it." >&2
        mkdir -p $1
    fi
}
```
