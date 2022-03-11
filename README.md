## Sample Kraken Invocation

```bash
(
  cd documents/*/
  ketos segtrain -o ../../models/*/quran_segtrain -d cuda:0 -f alto -bl *.xml
  ketos train -d cuda:0 -f binary -o ../../models/*/quran_rectrain --augment ../../binary-dataset.bin
  ketos compile -o binary-dataset.bin -f alto --force-type baseline *.xml
  ketos test -f binary -d cuda:0 -m ../../models/*/quran_rectrain_37.mlmodel ../../binary-dataset.bin | tee ../../models/*/quran_rectrain_37.mlmodel.eval.log
)
```

After evaluation, 99.99% accuracy (see the `.eval.log` file for a list of errors and other details). Images, binary dataset and models included in repository as Git LFS objects. Also see [quran2gt3](https://github.com/sixtyfive/quran2gt3/) repository.
