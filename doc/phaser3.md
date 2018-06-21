калбэк create может содержать привязки, которые будут учитываться на update

### actions

    var group = this.add.group({
        key: 'diamonds',
        frame: [ 0, 1, 2, 3, 4 ],
        frameQuantity: 2
    });

Повторяет каждый элемент по 2. т.е. group.getChildren() даст последовательность:
[ 0, 0, 1, 1, 2, 2, 3, 3, 4, 4 ]

    Phaser.Actions.GridAlign(group.getChildren(), {
        width: 10,
        height: 10,
        cellWidth: 32,
        cellHeight: 32,
        x: 100,
        y: 100
    });

Делает сетку из последовательности. Удобно для табличного представления объектов.


    Phaser.Actions.IncX(groupA.getChildren(), Math.cos(move));
    Phaser.Actions.IncY(groupA.getChildren(), Math.sin(move));
    Phaser.Actions.Rotate(groupA.getChildren(), -0.01);
    move += 0.01;

Управление группой объектов

    var circle = new Phaser.Geom.Circle(400, 300, 110);
    Phaser.Actions.PlaceOnCircle(group.getChildren(), circle);

Расположение по кругу. Аналогично можно располагать по другим геометрическим фигурам.
Также есть возможность рандомного расположния внутри фигуры.

    tween = this.tweens.addCounter({
        from: 220,
        to: 1,
        duration: 1000,
        delay: 100,
        ease: 'Sine.easeInOut',
        repeat: -1,
        yoyo: false
    });
    
сжимает, и если yoyo - разжимает.

    p = new Phaser.Geom.Point(400, 300);
    Phaser.Actions.RotateAroundDistance(group.getChildren(), { x: 400, y: 300 }, 0.02, 200);
    Phaser.Actions.RotateAroundDistance(group.getChildren(), p, 0.02, 200);
    
Вертеть вокруг точки или дистанции.

    this.input.on('pointermove', function (pointer) {
        p.setTo(pointer.x, pointer.y);
    });
    
Точку в свою очередь можно привязать к курсору, например (в create).

    Phaser.Actions.SetAlpha(group.getChildren(), 0, 1 / 50);

градация alpha для группы, начальное значение и шаг.

    Phaser.Actions.ShiftPosition(group.getChildren(), x, y);

последний перемещается на новую позицию

    rect = Phaser.Geom.Rectangle.Clone(this.cameras.main);
    Phaser.Actions.WrapInRectangle(shapes, rect, 72);

ограничение рисовки прямоугольником
