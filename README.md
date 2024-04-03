Implementation of Quill editor Delta format in Dart. Refer to official
[documentation][] for more details.

[documentation]: https://quilljs.com/docs/delta/

## Usage

```dart
import 'package:quill_format/quill_format.dart';

void main() {
  var doc = new Delta()..insert('Hello world', {'h': '1'});
  var change = new Delta()
    ..retain(6)
    ..delete(5)
    ..insert('Earth');
  var result = doc.compose(change);
  print('Original document:\n$doc\n');
  print('Change:\n$change\n');
  print('Updated document:\n$result\n');

  /// Prints:
  ///
  ///     Original document:
  ///     ins⟨Hello world⟩ + {h: 1}
  ///
  ///     Change:
  ///     ret⟨6⟩
  ///     ins⟨Earth⟩
  ///     del⟨5⟩
  ///
  ///     Updated document:
  ///     ins⟨Hello ⟩ + {h: 1}
  ///     ins⟨Earth⟩
}
```