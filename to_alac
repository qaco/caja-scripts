#!/bin/bash

free=$CAJA_SCRIPT_SELECTED_FILE_PATHS
if [ ! -d $free ]; then
    zenity --info --text="$free is not a directory" --title="alac mass convertor"
else
    target="$free (ALAC)"
    mkdir "$target"
    cd "$(echo $free | sed -e "s/(/\(/g")"
    for d in `find . -type d`; do
        for f in "$d"/*.{mp3,MP3,flac,FLAC}; do
            if [ -f "$f" ]; then
                name=$(basename "$f")
                ffmpeg -i "$f" -loglevel quiet -acodec alac "$target/${name%.*}.m4a"
            fi
        done
    done
    zenity --info --text="conversion done" --title="alac mass convertor"
fi
